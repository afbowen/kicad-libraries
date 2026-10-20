# KiCad Board Setup Templates

Reusable PCB design settings for fabrication through JLCPCB.

## Templates

| Project | Stackup |
|---|---|
| `jlcpcb_2l_1.6mm_1oz` | 2-layer, 1.6 mm, 1 oz copper |
| `jlcpcb_2l_1.6mm_2oz` | 2-layer, 1.6 mm, 2 oz copper |

## Usage

1. Open your target PCB in KiCad PCB Editor.
2. Navigate to **File → Board Setup → Import Settings from Another Board**.
3. Select the appropriate template's `.kicad_pcb` file.
4. Import stackup, design rules, net classes, and other desired settings.

**Note:** These are starting configurations, not substitutes for verifying JLCPCB manufacturing capabilities and running DRC before fabrication.
