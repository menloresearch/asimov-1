# Mechanical fabrication

Robot fabrication files are organized by subassembly and manufacturing process/material. The generated [CSV](FABRICATION_MANIFEST.csv) and [JSON](FABRICATION_MANIFEST.json) manifests inventory STEP and STL files under `ASV1/*/FABRICATION/*/`. Accessories are documented below, with their fabrication notes and quantities.

## Layout

```text
mechanical/
├── ASV1/
│   ├── 100/ ... 700/
│   │   └── FABRICATION/<process_material>/<part>.STEP or .STL
│   ├── FullBodyAssembly/Asimov_1.STEP
│   └── Docs/
├── accessories/
│   ├── dummy_hands/           ASV1_DUMMY_HANDS.3mf with embedded print settings
│   ├── shoes/                 ASV1_Shoes.STL; print 2 identical copies
│   └── stool/                 CAD, separate BOM, and fabrication notes
├── FABRICATION_MANIFEST.csv
└── FABRICATION_MANIFEST.json
```

## Part naming

![Asimov 1 part naming convention, subassembly codes, and manufacturing methods](naming_convention.png)

## Fabrication classes

| Directory | Process | Material |
|---|---|---|
| `ALU_7075` | CNC machining | Aluminium 7075 |
| `SML_316L` | Metal 3D printing (SLM) | Stainless steel 316L |
| `MJF_PA12` | Multi Jet Fusion | PA12 nylon |
| `OFF_THE_SHELF` | Purchase | See the BOM / supplier specification |

The existing `SML_316L` directory spelling is retained in the inventory. The part-naming chart above describes the robot part-number structure; each part's fabrication notes provide its material specification.

## Accessories

### Shoe soles

The [shoes](accessories/shoes/README.md) use a single symmetric [ASV1_Shoes.STL](accessories/shoes/ASV1_Shoes.STL) that fits either foot. **Print two identical copies**, one per foot, in TPU Shore 95A using FDM. The STL units are millimetres; print at 100% scale with the sole on the bed.

The shoe notes include the full print settings and slip-on attachment using two M4 × 16 mm flat-head bolts per foot, with no adhesive. Compatibility is confirmed for the latest foot design in this repository as of 2026-11-04.

### Dummy hands

The [dummy hands](accessories/dummy_hands/README.md) are supplied as [ASV1_DUMMY_HANDS.3mf](accessories/dummy_hands/ASV1_DUMMY_HANDS.3mf), a print-ready Bambu Studio project. Open it as a project to use its embedded printing settings and plate layout.

### Stool accessory

The [stool](accessories/stool/README.md) has its own [BOM](accessories/stool/BOM.csv), including quantities, CAD paths, and sourcing details. Print components 001–003 in PLA or PETG using FDM; the stool notes contain the print settings. Use two aluminium 40 × 40 mm extrusions, each cut to 500 mm with no end machining.

## Updating the manifests

From the repository root:

```bash
python3 scripts/generate_fabrication_manifest.py
python3 scripts/generate_fabrication_manifest.py --check
```

Commit both generated outputs alongside fabrication-file changes. The manifest records file inventory; use the part documentation and BOMs for quantities and manufacturing instructions.

## File storage

Uppercase `.STEP` files and `.3mf` projects use Git LFS. The shoe STL and small documents use ordinary Git. Keep the original supplier/archive packages in the ignored root `temp/` folder while preparing contributions.

Hardware files are covered by the repository's [CERN-OHL-S-2.0 hardware license](../HARDWARE-LICENSE.txt).
