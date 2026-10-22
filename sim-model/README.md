# Simulation Model

URDF and MuJoCo models for two Asimov v1 configurations:

- `asimov_1_25dof`: 25 revolute joints and 26 STL meshes; its links match the shared links of the 27-DOF model (joint zero angles keep the 25-DOF convention). The MJCF has a floating base and friction-tuned foot contacts for locomotion training. Actuators are configured by the training code.
- `asimov_1_27dof`: 27 body joints plus two gripper drivers and ten coupled gripper joints, using 42 meshes. The MJCF has a fixed base, primitive collision geoms (body and foot geoms shared with the 25-DOF model, plus forearm and gripper primitives), gripper coupling constraints, and two gripper motors.

## Contents

```
sim-model/
├── asimov_1_25dof/
│   ├── urdf/
│   │   └── asimov_1_25dof.urdf
│   ├── xml/
│   │   └── asimov_1_25dof.xml
│   └── meshes/          26 STL meshes
└── asimov_1_27dof/
    ├── urdf/
    │   └── asimov_1_27dof.urdf
    ├── xml/
    │   └── asimov_1_27dof.xml
    └── meshes/          42 STL meshes
```

Each variant's URDF and MJCF share its `meshes/` directory. All asset paths are relative to the model files. The 27-DOF waist and gripper base STLs are decimated to 195,000 triangles to stay under MuJoCo's 200,000-triangle STL limit (max surface deviation < 0.7 mm). Keep any re-exported mesh under that limit.

## Usage

From `sim-model/`, open either MJCF:

```bash
python3 -m mujoco.viewer --mjcf=asimov_1_25dof/xml/asimov_1_25dof.xml
python3 -m mujoco.viewer --mjcf=asimov_1_27dof/xml/asimov_1_27dof.xml
```

Validated with [MuJoCo](https://mujoco.org/) 3.4.0. The URDF files also include MuJoCo compiler settings to resolve their relative mesh paths and retain visual geometry when imported directly.

## Resources

- [Locomotion Control guide](https://manual.asimov.inc/v1/locomotion) — policy training, control modes, and hardware-in-the-loop setup
- [Asimov API](https://manual.asimov.inc/v1/api) — deploy policies to the real robot
- [Discord](https://discord.gg/HzDfGN7kUw) — questions and discussion
