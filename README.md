# Sand Game Pro · Advanced Simulation v2.0

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Pages-Deployed-success.svg)](https://github.com/)
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/)](https://github.com/)

Ein interaktives **Zellulares Automaten-Spiel** mit physikalisch, chemisch und biologisch fundierter Simulation. Erstelle Sand, Wasser, Feuer, Pflanzen, Pilze und mehr – und beobachte, wie sie interagieren.

## 🎮 Features

### Materialien (58+)

| Kategorie | Materialien |
|-----------|-------------|
| **Grundlagen** | Sand, Stein, Erde, Wasser, Luft |
| **Flüssigkeiten** | Wasser, Öl, Lava, Säure, Schmelze |
| **Gase** | Dampf, CO₂, Stickstoff, H₂, O₂ |
| **Energie** | Feuer, Funke, TNT, Feuerlöscher |
| **Biologie** | Pflanzen, Blumen, Sporen, Schimmel, Bakterien |
| **Chemie** | Salz, Kalk, Kohle, Metall, Glas |
| **Kunststoffe** | Kunststoff (PLASTIC) |
| **Spezial** | Eier, Beton, Isolator, Sensor |

### Physikalische Simulation

- **Thermodynamik**: Wärmeleitung, Wärmekapazität, Phasenübergänge (Schmelzen, Sieden, Kondensieren)
- **Dichte-basierte Physik**: Materialien schichten sich korrekt (Gas < Flüssigkeit < Festkörper)
- **Strömungsmechanik**: Flüssigkeiten und Pulver verhalten sich realistisch
- **Explosionsphysik**: Zonen-basierte Blastwirkung mit Verdampfung, Verbrennung und Rauchentwicklung

### Chemische Reaktionen

- **Verbrennung**: H₂ + O₂ → H₂O (Wasser/Dampf) mit Energie freisetzung
- **Neutralisation**: Säure + Lauge → Salz + Wasser
- **Oxidation**: Metall rostet bei Feuchtigkeit
- **Reduktion**: Erz wird zu Metall geschmolzen
- **Ei-Coagulation**: Protein gerinnt bei 62°C

### Biologische Prozesse

- **Photosynthese**: Pflanzen nutzen Licht, Wasser und CO₂ für Wachstum
- **Transpiration**: Wasserverdunstung durch Blätter
- **Nährstoffaufnahme**: Wurzeln scanzen Boden auf Nährstoffe
- **Tropismen**: Pflanzen wachsen zum Licht
- **Sporen-Verbreitung**: Schimmel und Pilze verbreiten sich über Luft und Feuchtigkeit
- **Keimung**: Sporen keimen nur bei ausreichender Feuchtigkeit

## 🚀 Schnellstart

### Lokal ausführen

1. Klone das Repository:

   ```bash
   git clone https://github.com/yourusername/sand-game.git
   ```

2. Öffne [`sand_game.html`](sand_game.html) in einem modernen Browser (Chrome, Firefox, Edge)
3. Wähle ein Material aus der Palette und male auf das Spielfeld!

### Online spielen

Das Spiel kann über [GitHub Pages](https://yourusername.github.io/sand-game/) gespielt werden.

## 🎛️ Steuerung

### Maus

| Aktion | Bedienung |
|--------|-----------|
| Zeichnen | Linke Maustaste gedrückt halten |
| Radieren | Rechte Maustaste gedrückt halten |
| UI ein/aus | `H` Taste |
| Spielfeld leeren | `C` Taste |
| Pause | `P` Taste |

### Einstellungen

| Einstellung | Bereich | Standard |
|-------------|---------|----------|
| **Grid-Auflösung** | 50–500 Zellen/Breite | 200 |
| **Pinselgröße** | 1–30 Pixel | 5 |
| **Simulations-Ticks pro Frame** | 1–10 | 5 |

## 🔬 Wissenschaftliche Grundlagen

### Pflanzen-Physiologie

Das Wachstum von Pflanzen folgt realistischen biologischen Modellen:

```
Wachstumsrate = Basis × min(1, Wasser/3) × min(1, Nährstoffe/2) × Photosynthese × Temperaturfaktor
```

- **Optimale Temperatur**: 10–30°C
- **Temperaturstress**: Wachstum reduziert außerhalb des optimalen Bereichs
- **Lichtabhängigkeit**: Nachts nur 5% der tagaktiven Wachstumsrate
- **Wasserhaushalt**: Transpiration bei Trockenheit reduziert Wachstum

### Explosions-Physik

TNT-Explosionen verwenden ein **Zonen-Modell**:

| Zone | Intensität | Effekt |
|------|-----------|--------|
| Zentrum | > 0.7 | Verdampfung aller Materialien |
| Innerer Ring | 0.4–0.7 | Verbrennung und Schmelzen |
| Äußerer Ring | < 0.4 | Hitze, Rauch, leichte Verschiebung |

### Lava-Kühlung

Lava kühlt je nach Untergrund unterschiedlich schnell ab:

| Untergrund | Kühlrate | Spezial-Effekt |
|------------|----------|----------------|
| Wasser/Eis | 2.0 | Bildung von Obsidian (GLASS) bei < 800°C |
| Erde/Sand | 0.3 | Bildung von Stein (STONE) bei < 600°C |
| Luft | 0.1 | Langsame Abkühlung |

## 📁 Projektstruktur

```
sand-game/
├── .github/
│   └── workflows/
│       └── build.yml          # CI/CD Pipeline
├── sand_game.html             # Hauptanwendung (Single-File)
└── README.md                  # Diese Datei
```

> **Hinweis**: Dies ist eine Single-File-Anwendung. Alle Logik, Rendering und UI sind in einer einzigen HTML-Datei enthalten.

## 🧪 Materialien-Leitfaden

### Dichte-Klassen

```
TYPE.GAS       (Dichte 0-5)    → Steigen nach oben
TYPE.LIQUID    (Dichte 5-20)   → Fließen unter Festkörpern
TYPE.POWDER    (Dichte 20-50)  → Fließen wie Sand
TYPE.SOLID     (Dichte 50+)    → Bleiben an Ort und Stelle
```

### Temperatur-Eigenschaften

Jedes Material hat definierte:

- **Schmelzpunkt** (`melting`): Temperatur, bei der es schmilzt
- **Siedepunkt** (`boiling`): Temperatur, bei der es verdampft
- **Wärmeleitfähigkeit** (`conductivity`): Wie schnell Wärme weitergegeben wird
- **Wärmekapazität** (`heatCapacity`): Wie viel Energie gespeichert wird

## 🛠️ Entwicklung

### Code-Struktur

```javascript
// Material-Definition
const SAND = 1;
materials[SAND] = {
  id: SAND,
  name: "Sand",
  type: TYPE.POWDER,
  color: [220, 200, 160],
  density: 30,
  melting: 1710,
  boiling: 2500,
  // ... weitere Eigenschaften
};

// Update-Funktion für jedes Material
function updateSand(x, y) {
  // Physik-Logik...
}

// Haupt-Loop
function frame() {
  update();  // Simulation
  render();  // Canvas-Rendering
}
```

### Erweitern um neue Materialien

1. Neue Material-Konstante hinzufügen: `const MY_MATERIAL = 53;`
2. Material-Definition in `materials` Array eintragen
3. Optional: Update-Funktion für spezielles Verhalten schreiben
4. Zur Material-Palette in der UI hinzufügen

## 📄 Lizenz

Dieses Projekt steht unter der [MIT License](LICENSE).

## 🙏 Credits

Entwickelt als zellulares Automaten-Spiel mit Fokus auf wissenschaftliche Korrektheit.

**Technologien**: Vanilla JavaScript, HTML5 Canvas, CSS3

---

*„Die einzige sichere Annahme ist, dass unsere Annahmen falsch sind."* – Wissenschaftliches Mantra
