# Projektstruktur: TIROLER Einbruchdiebstahlversicherung Training

## Übersicht

Interaktives Web-Training zur Einbruchdiebstahlversicherung für TIROLER Mitarbeiter, aufgebaut als Action-Adventure Game.

## Projektstruktur

```
Einbruchdiebstahlversicherung/
├── index.html              # Haupt-Applikation (Single Page Application)
├── README.md               # Ursprüngliche Trainingsinhalte
├── Claude.md               # Diese Datei - Projektdokumentation
└── .github/
    └── workflows/
        └── deploy.yml      # GitHub Pages Deployment
```

## Technologie-Stack

- **HTML5** - Struktur der Anwendung
- **CSS3** - Styling mit CSS Variables, Animationen, Responsive Design
- **Vanilla JavaScript** - Spiellogik ohne externe Abhängigkeiten
- **GitHub Pages** - Hosting und Deployment

## Architektur

### Single Page Application

Die gesamte Anwendung ist in einer einzigen HTML-Datei (`index.html`) implementiert:

- **Kein Build-Prozess erforderlich** - direktes Deployment möglich
- **Keine externen Abhängigkeiten** - offline-fähig
- **Schnelle Ladezeiten** - alles in einer Datei

### Komponenten

#### 1. Screens (Ansichten)
- `#start-screen` - Startbildschirm mit Spielstart
- `#map-screen` - Level-Auswahl (4 Level)
- `#level-1` bis `#level-4` - Lerninhalt und Quiz pro Level
- `#completion-screen` - Abschlussbildschirm mit Zusammenfassung

#### 2. Game State
```javascript
gameState = {
    currentLevel: 0,          // Aktuelles Level
    xp: 0,                    // Erfahrungspunkte
    maxXp: 400,               // Max XP für Anzeige
    completedLevels: [],      // Abgeschlossene Level
    quizProgress: {},         // Quiz-Fortschritt pro Level
    levelQuizCounts: {        // Anzahl Quiz-Fragen pro Level
        1: 2, 2: 3, 3: 3, 4: 4
    }
}
```

#### 3. UI-Elemente
- **Header** - XP-Anzeige, Level-Indikator
- **Partikel-Animation** - Dekorative Hintergrund-Animation
- **Charakter-Helfer** - Interaktiver Tipp-Geber
- **Progress-Bars** - Fortschrittsanzeige pro Level

### Level-Struktur

| Level | Thema | Quiz-Fragen | XP möglich |
|-------|-------|-------------|------------|
| I | Grundlagen | 2 | 100 |
| II | Ausschlüsse | 3 | 125 |
| III | Pflichten | 3 | 125 |
| IV | Vertrag | 4 | 150 |

**Bonus:** 50 XP pro abgeschlossenem Level

### CSS-Design-System

#### Farben (CSS Variables)
```css
--primary: #1a1a2e    /* Dunkler Hintergrund */
--secondary: #16213e  /* Sekundärer Hintergrund */
--accent: #e94560     /* Akzentfarbe (Rot) */
--gold: #ffd700       /* Gold für Highlights */
--success: #4ade80    /* Richtige Antwort */
--error: #ef4444      /* Falsche Antwort */
```

#### Responsive Breakpoints
- Desktop: > 768px (volle Darstellung)
- Mobile: <= 768px (angepasstes Layout, versteckte Stats)

## Deployment

### GitHub Pages

Das Deployment erfolgt automatisch über GitHub Actions:

1. Push auf `main` oder `master` Branch
2. Workflow `.github/workflows/deploy.yml` wird ausgelöst
3. Statische Dateien werden zu GitHub Pages hochgeladen

### Manuelles Deployment

1. Repository in GitHub Pages aktivieren (Settings > Pages)
2. Source: "GitHub Actions" auswählen
3. Workflow wird bei Push automatisch ausgeführt

### Lokale Entwicklung

```bash
# Einfacher HTTP-Server (Python)
python -m http.server 8000

# Oder mit Node.js
npx serve .
```

## Erweiterungsmöglichkeiten

- **Persistenz**: LocalStorage für Spielstand-Speicherung
- **Mehr Level**: Zusätzliche Trainingsmodule
- **Leaderboard**: Highscore-System
- **Animationen**: Erweiterte Übergangseffekte
- **Audio**: Sound-Effekte und Hintergrundmusik
- **Zertifikat**: PDF-Generierung bei Abschluss

## Wartung

### Inhalt aktualisieren

1. Quiz-Fragen: Im entsprechenden Level-Abschnitt in `index.html`
2. Lerninhalte: In den `.content-box` Elementen
3. Tipps: Im `tips` Array im JavaScript-Teil

### Styling anpassen

CSS Variables am Anfang der `<style>` Section ändern für globale Anpassungen.
