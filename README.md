# Planetary Annihilation Extension Interface On Units (PAEIOU)

This is a Python script that allows one to easily generate Planetary Annihilation mods that add units to the game. It is currently in a very early state, and is neither complete nor well-documented.

Support will **NOT** be offered for PAEIOU under any circumstances until documentation is complete.

## Current State
PAEIOU currently does not allow one to generate split server/client companion mods.

## Format

By default, PAEIOU expects the following files in each unit folder:
- `unit.json`
- `si.png`
- `img.png`
- `build.json`

`unit.json` is the unit's json file.

`si.png` is the unit's strategic icon as a png file.

`img.png` is the unit's buildbar icon as a png file.

`build.json` is a custom PAEIOU file that indicates where the unit appears on the build bar.

If the unit has a weapon or custom effect files, PAEIOU expects that all weapon, ammo, and effect files will have the ".json" or ".pfx" extension.

If the unit has a custom model, it is expected that this model 

In addition, you may change these defaults by including an optional  file, `meta.json`, which can have the following fields, in any order:
```
{
    "unit": "(filename)" | false,
    "si": "(filename)" | false,
    "img": "(filename)" | false,
    "build": "(filename)" | false,
    "additional": ["other non-json, non-pfx files here, in an array"]
}
```

If `"unit"` is set to `false`, the unit will not be added to the unit list. If it is set to a string, it instead specifies an alternative filename for the unit. This filename does **NOT** need to have extension `.json`, but this is **NOT** true for additional `.json` or `.pfx` files.

If `"si"` is set to `false`, the unit will not have a custom strategic icon. If it is set to a string, it instead specifies an alternative filename for the strategic icon.

If `"img"` is set to `false`, the unit will not have a custom buildbar image. If it is set to a string, it instead specifies an alternative filename for the buildbar image.

If `"build"` is set to `false`, the unit will not be buildable. If it is set to a string, it instead specifies an alternative filename for PAEIOU's `build.json`.

For an example where some of these settings may be useful, consider the situation of adding an additional strategic icon through PAEIOU without adding a whole unit, one can use:
```
{
    "unit": false,
    "img": false,
    "build": false
}
```


## Future Goals
Allow one to merge multiple PAEIOU projects to generate composite mods without additional scripting (although this is currently enabled by just moving all of the PAEIOU projects' units into the same folder and concatenating `unit_add_list.txt`.