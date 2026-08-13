# Simulation Model

MuJoCo model for Asimov v1. Floating base with 23 hinge joints, 25 STL link meshes, friction-tuned foot contacts. Built for locomotion policy training and hardware-in-the-loop testing. No actuators are defined in the XML — the training sim configures them in Python.

## Contents

```
sim-model/
├── xmls/asimov_1.xml     Full robot model (MJCF)
├── urdf/asimov_1.urdf    URDF description (shares the same meshes)
└── assets/meshes/        25 STL link meshes
```

## Usage

```bash
python3 -m mujoco.viewer --mjcf=sim-model/xmls/asimov_1.xml
```

Requires [MuJoCo](https://mujoco.org/) 3.x.

## Resources

- [Locomotion Control guide](https://manual.asimov.inc/v1/locomotion) — policy training, control modes, and hardware-in-the-loop setup
- [Asimov API](https://manual.asimov.inc/v1/api) — deploy policies to the real robot
- [Discord](https://discord.gg/HzDfGN7kUw) — questions and discussion
