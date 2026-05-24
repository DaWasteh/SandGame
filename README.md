# Sand Game Pro · Advanced Simulation v2.0

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Pages-Deployed-success.svg)](https://github.com/)
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/)](https://github.com/)

Ein interaktives **Zellulares Automaten-Spiel** mit physikalisch, chemisch und biologisch fundierter Simulation. Erstelle Sand, Wasser, Feuer, Pflanzen, Pilze und mehr – und beobachte, wie sie interagieren.

## 🎮 Features

### Materialien (72+)

| Kategorie | Materialien |
|-----------|-------------|
| **Grundlagen** | Sand, Stein, Erde, Wasser, Luft |
| **Flüssigkeiten** | Wasser, Öl, Lava, Säure, Schmelze |
| **Gase** | Dampf, CO₂, Stickstoff, H₂, O₂, Pollen |
| **Energie** | Feuer, Funke, TNT, Feuerlöscher |
| **Biologie** | Samen, Keimlinge, Stämme, Blätter, Wurzeln, 3 Blütentypen, Pilze, Bakterien |
| **Chemie** | Salz, Kalk, Kohle, Metall, Glas |
| **Kunststoffe** | Kunststoff (PLASTIC) |
| **Spezial** | Eier, Beton, Isolator, Sensor, Strahlung |

### 🌱 Erweitertes Biologie-System (v2.1)

#### Wachstumsstadien
Pflanzen durchlaufen strukturierte Entwicklungsstadien:

```
SAMEN → KEIMLING → JUNGER STAMM → ERWACHSENE PFLANZE → BLÜTE → ALTERUNG → TOTE PFLANZE → KOMPOST
```

| Stadium | Material | Beschreibung |
|---------|----------|--------------|
| 0 | [`PLANT_SEED`](sand_game.html:307) | Samen keimt bei Feuchtigkeit (5-30°C) |
| 1 | [`PLANT_SPROUT`](sand_game.html:308) | Keimling bildet erste Wurzeln und Blätter |
| 2 | [`PLANT_STEM`](sand_game.html:308) | Haupttrieb wächst nach oben, seitliche Blätter |
| 3 | [`PLANT_MATURE`](sand_game.html:309) | Erwachsene Pflanze, kann Blüten bilden |
| 4 | [`FLOWER_DANDELION`](sand_game.html:310) | Gänseblümchen (gelb) |
| 4 | [`FLOWER_TULIP`](sand_game.html:310) | Tulpe (rot) |
| 4 | [`FLOWER_POPPY`](sand_game.html:311) | Mohn (orange-rot) |
| 5 | [`PLANT_DEAD`](sand_game.html:311) | Tote Pflanze, wird zu Kompost |

#### Strukturierter Wachstum
- **Klarer Haupttrieb**: Pflanzen wachsen kontrolliert nach oben
- **Seitliche Blätter**: Alle 8-12 Ticks entsteht ein Blatt links/rechts abwechselnd
- **Kein Wuchern**: Keine seitlichen Stamm-Äste mehr
- **Wurzeln**: Nur der Keimling bildet Wurzeln nach unten

#### Saison-System
4 Jahreszeiten mit Einfluss auf das Wachstum:

| Saison | Symbol | Wachstumsfaktor | Effekt |
|--------|--------|-----------------|--------|
| Frühling | 🌸 | 1.0 | Normales Wachstum |
| Sommer | ☀️ | 1.2 | Maximales Wachstum |
| Herbst | 🍂 | 0.5 | Reduziertes Wachstum, Blätter färben sich |
| Winter | ❄️ | 0.1 | Fast kein Wachstum, Pflanzen sterben langsam |

#### Säfte- und Nährstoffdynamik
- [`plantSapGrid`](sand_game.html:510) - Säftestand (0-100)
- [`soilNutrientGrid`](sand_game.html:511) - Bodennährstoffe (0-100)
- [`plantWaterGrid`](sand_game.html:512) - Wasserstand (0-100)
- Wurzeln absorbieren Wasser und Nährstoffe aus dem Boden
- Saft wird nach oben zu Blättern und Blüten transportiert

#### Kompostierung
- Tote Pflanzen bleiben **200+ Ticks** liegen
- Natürliche Zersetzung: **0.0002 pro Tick** (ca. 16 Minuten bei 5 Ticks/Frame)
- Mit Bakterien/Schimmel: **0.001-0.002 pro Tick**
- Nährstoffe werden langsam an den Boden zurückgegeben

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
- **Nährstoffaufnahme**: Wurzeln scanken Boden auf Nährstoffe
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
| **Grid-Auflösung** | 50–320 Zellen/Breite | 200 |
| **Pinselgröße** | 1–30 Pixel | 5 |
| **Simulations-Ticks pro Frame** | 1–8 | 5 |

## 📸 Bild-Import

Das Spiel unterstützt den Import von Bildern zur Erstellung von Simulationen:

1. Klicke auf **"📁 Bild importieren"** im UI
2. Wähle ein Bild aus (JPG, PNG)
3. Das Bild wird automatisch in Materialien umgewandelt
4. Klicke auf **"Zuordnung anwenden"** um das Bild im Grid zu platzieren
5. Klicke auf **"Simulation starten"** um die Simulation zu beginnen

## 🔬 Wissenschaftliche Grundlagen

### Pflanzen-Physiologie

Das Wachstum von Pflanzen folgt realistischen biologischen Modellen:

```
Wachstumsrate = Basis × min(1, Wasser/3) × min(1, Nährstoffe/2) × Photosynthese × Temperaturfaktor
```

- **Optimale Temperatur**: 10–35°C
- **Temperaturstress**: Wachstum reduziert außerhalb des optimalen Bereichs
- **Lichtabhängigkeit**: Nachts nur 5% der tagaktiven Wachstumsrate
- **Wasserhaushalt**: Transpiration bei Trockenheit reduziert Wachstum

### Sonnenzyklus

Das Spiel simuliert einen Tag/Nacht-Zyklus mit:

- **Tag (50% des Zyklus)**: Volle Sonnenintensität für Photosynthese
- **Nacht (50% des Zyklus)**: Schwaches Mondlicht, Pflanzen atmen CO₂ aus
- **Sonnenhöhe**: Sinusförmiger Verlauf für sanfte Übergänge

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

*"Die einzige sichere Annahme ist, dass unsere Annahmen falsch sind."* – Wissenschaftliches Mantra
