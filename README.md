# kicad-libraries
This repository contains component symbols, footprint, and 3D models to be used in KicAd projects.
All parts were created using KiCad 9.

**NOTE** that these libraries will **not** be referenced until KiCad paths (for your machine's
install, or at project level) are pointed to this submodule; see usage instructions below.


## Usage
This repo is best suited to be used as a submodule inside a KiCad project repository, or repository
of KiCad projects. To do so...

1. Clone this repository into your project repo.
   ```
   cd /path/to/kicad_project_repo
   git submodule add git@github.com:<user>/kicad-libraries.git
   git commit -m "Add kicad-libraries submodule"
   ```

2. In KiCad, create a environment variable path to the `kicad-libraries` submodule using
   `Preferences → Configure Paths...`
   - Example
     - Name: `{KICAD_LIB}`
     - Path: `/home/$USER/git/kicad-projects/kicad-libraries`

3. In KiCad, manage symbol and footprint libraries at the global or project level as needed.
   - Many projects will have these defined at the project level, so as long as the `{KICAD_LIB}`
     environment variable is defined as the correct path, **this step should not be necessary**.
   - Example: Symbol
     - `Preferences → Manage Symbol Libraries...`
     - Nickname: `Custom_DCDC`
     - Library Path: `${KICAD_LIB}/symbols/Custom_DCDC.kicad_sym`
   - Example: Footprint
     - `Preferences → Manage Footprint Libraries...`
     - Nickname: `Custom_DCDC`
     - Library Path: `${KICAD_LIB}/footprints/Custom_DCDC.pretty`
   - Example: 3D Model
     - `Footprint Editor → Footprint Properties → 3D Models → 3D Model(s)`
     - 3D Path: `${KICAD_LIB}/3dmodels/Custom_DCDC.step`


##  Generics
This is a KiCad project consisting only of schematic sheets containing generic parts. These are the
parts from KiCad's built-in libraries, where you'd typically drop a generic resistor symbol, assign
it a value, link it to a stock footprint, then create fields for MPN and manufacturer after finding
an option on Digi-Key, etc.

Instead, this project is a quick grab-and-go solution for building new designs. Simply...

1. Open the sheet containing the part you're after (e.g. `cap_0603` for 0603-sized capacitors)
2. Copy the symbol (click on it then `Ctrl+C`)
3. Paste it into your new schematic

This gets you a symbol with target value set, tied to a footprint with 3D model, and assigned a
part number and manufacturer for your BOM.

If you ever add a new part to your project from generic KiCad libraries, add it to the `generics`
project for future use.

Likewise, if you ever find an MPN is no longer stocked or in production, update the MPN on the part
in the `generics` project.

### Important Notes
All units are imperial (e.g. 0603 is imperial, corresponds to 1608 metric).

If parts in the `generics` project are updated, those updates will **not** be reflected in projects
they were copied into.

This project-based approach is **not** the best way to do this. It should eventually move in the
direction of becoming a proper database, but this facilities quick development with much less lift
in the mean time.
