## Robot Processing Unit 
### Motion Control Board
- The Motion Control Board (MCB) is a carrier board designed for the Radxa CM5. It has an onboard IMU and contains the necessary motor communication buses for the robot to function.
- The Power Distribution Board (PDB) sits on top of the Motion Control Board (MCB) to form the 2 board stackup.

General information:
- Power is supplied via the XT90(2+2) connector on the PDB, with 5V being routed to the MCB at the bottom
- The UART TTL debug lines have been fanned out as test pads on the PDB for debugging purposes.
- The LSM6DSV IMU is located at the bottom of the MCB
- LCSC component IDs are attached in the KiCad source files for direct JLCPCB fabrication and assembly.

### Communication Ports

| Port Type | Quantity | Details |
|-----------|----------|---------|
| CAN (SPI-CAN) | 6 | CAN via SPI bridge |
| USB 2.0 | 2 | USB interfaces |
| Ethernet | 1 | 1Gbps |
| I2C | 1 | I2C interface |

### Port Mapping

| Port ID | Purpose |
|---------|---------|
| LL | Left leg bus |
| RL | Right leg bus |
| LA | Left arm bus |
| RA | Right arm bus |
| NP | Neck pitch connection for the torso bus |
| NY | Neck yaw connection for the torso bus |
| W  | Waist yaw connection for the torso bus |

> Please refer to the KiCAD source files for a detailed view of all pin mappings on the PDB

## Media Unit

The head of the robot contains a RPI5, with 2 boards to support its function.

Head board:
- contains buck converters to power the RPI5 with 5V
- an audio IC to handle the stereo microphones and stereo speakers, although only 1 speaker output is currently used

RPI5 Hat:
- a small hat that allows for a clean 5V connection to the headers of the RPI5
- contains a button, LED and buzzer for basic status messages, similar to a consumer motherboard

## Wiring

- Each line refers to a pre-made cable on the robot
- Certain connections can only be complete post assembly due to space contraints. These connections have been marked with the Joint names WAGO or SOLDER.

> If making cables from scratch, double-check wire pathing to make sure there is sufficient slack on each connection.



