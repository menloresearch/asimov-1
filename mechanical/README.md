# Mechanical fabrication

Robot fabrication files are organized by subassembly and manufacturing process/material. The generated [CSV](FABRICATION_MANIFEST.csv) and [JSON](FABRICATION_MANIFEST.json) manifests inventory STEP and STL files under `ASV1/*/FABRICATION/*/`.

## Layout

```text
mechanical/
├── ASV1/
│   ├── 100/ ... 700/
│   │   └── FABRICATION/<process_material>/<part>.STEP or .STL
│   ├── FullBodyAssembly/Asimov_1.STEP
│   └── Docs/
├── accessories/
│   └── stool/                 CAD, separate BOM, and fabrication notes
├── FABRICATION_MANIFEST.csv
└── FABRICATION_MANIFEST.json
```

| Subassembly | Module |
|---|---|
| 100 | Torso |
| 200 | Waist / pelvis |
| 300 | Right arm |
| 400 | Left arm |
| 500 | Right leg |
| 600 | Left leg |
| 700 | Head |

## Fabrication classes

| Directory | Process | Material |
|---|---|---|
| `ALU_7075` | CNC machining | Aluminium 7075 |
| `SML_316L` | Metal 3D printing (SLM) | Stainless steel 316L |
| `MJF_PA12` | Multi Jet Fusion | PA12 nylon |
| `FDM_TPU_95A` | FDM 3D printing | TPU, Shore 95A |
| `OFF_THE_SHELF` | Purchase | See the BOM / supplier specification |

The existing `SML_316L` directory spelling is retained in the inventory. Refer to the [part-naming chart](naming_convention.png) for the established part-number structure and to each part's fabrication notes for its material specification.

### Shoe soles

| Module | Part | Quantity per robot |
|---|---|---|
| 500 (right leg) | [ASV1_500_40D](ASV1/500/FABRICATION/FDM_TPU_95A/README.md) | 1 |
| 600 (left leg) | [ASV1_600_40D](ASV1/600/FABRICATION/FDM_TPU_95A/README.md) | 1 |

The same sole fits either foot. Both STL files contain identical geometry; print two copies in TPU 95A using FDM. The material hardness is **Shore 95A**; `40D` is retained as part of the supplied identifier. The STL units are millimetres; print at 100% scale with the sole on the bed. The linked part notes include the full print settings and slip-on attachment using two M4 × 16 mm flat-head bolts per foot, with no adhesive. Compatibility is confirmed for the latest foot design in this repository as of 2026-11-04.

### Stool accessory

The [stool](accessories/stool/README.md) has its own [BOM](accessories/stool/BOM.csv), including quantities, CAD paths, and sourcing details. Print components 001–003 in PLA or PETG using FDM; the stool notes contain the print settings. Use two aluminium 40 × 40 mm extrusions, each cut to 500 mm with no end machining. Accessory parts are inventoried there rather than under a robot subassembly.

## Updating the manifests

From the repository root:

```bash
python3 scripts/generate_fabrication_manifest.py
python3 scripts/generate_fabrication_manifest.py --check
```

Commit both generated outputs alongside fabrication-file changes. The manifest records file inventory; use the part documentation and BOMs for quantities and manufacturing instructions.

## File storage

Uppercase `.STEP` files follow the repository's Git LFS rule. The shoe STL files and small documents use ordinary Git. Keep the original supplier/archive packages in the ignored root `temp/` folder while preparing contributions.

Hardware files are covered by the repository's [CERN-OHL-S-2.0 hardware license](../HARDWARE-LICENSE.txt).
