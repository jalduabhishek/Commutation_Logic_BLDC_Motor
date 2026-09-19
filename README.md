# Commutationlogic_BLDC-motor

## Overview

This project implements the **commutation logic of a Brushless DC (BLDC) motor** using MATLAB and Simulink.  
The Simulink model generates the required inverter switching sequence, while the MATLAB script provides a dynamic visualization of the **three-phase commutation and rotor position**.

The project demonstrates the working of **six-step commutation** used for controlling a three-phase BLDC motor.

## Features

- Designed BLDC motor **six-step commutation logic** using MATLAB/Simulink.
- Implemented switching control for a **three-phase inverter with six switches**.
- Generated six different switching states for sequential phase excitation.
- Visualized phase A, B, and C excitation with a 120° phase displacement.
- Animated rotor position using angular data obtained from the Simulink model.
- Integrated MATLAB visualization with Simulink simulation outputs.
- Demonstrated the relationship between rotor position and inverter switching states.

## Six-Step Commutation Sequence

The inverter follows six switching states:

| Step | Switching Pattern |
|------|-------------------|
| 1 | `[1 0 0 0 0 1]` |
| 2 | `[0 0 1 0 0 1]` |
| 3 | `[0 1 1 0 0 0]` |
| 4 | `[0 1 0 0 1 0]` |
| 5 | `[0 0 0 1 1 0]` |
| 6 | `[1 0 0 1 0 0]` |

At each commutation step, two motor phases are energized while the remaining phase is inactive.

## Phase Arrangement

The three motor phases are separated by **120°**:

- Phase A → `0°`
- Phase B → `+120°`
- Phase C → `-120°`

The MATLAB visualization uses:

- **Red** → Active phase with one polarity
- **Blue** → Active phase with opposite polarity
- **White** → Inactive/Floating phase

## Working Principle

The overall operation of the project is:

1. Open the BLDC commutation Simulink model.
2. Run the simulation.
3. Obtain the inverter switching pattern from `switchPattern`.
4. Obtain rotor angular position from `thetaSim`.
5. Identify the current six-step commutation state.
6. Update the excitation of phases A, B, and C.
7. Update the rotor position.
8. Repeat the process for the complete simulated data.
9. Display the commutation sequence as a MATLAB animation.

## MATLAB–Simulink Integration

The Simulink model is opened and simulated using:

```matlab
mdl = 'Modeling_commutation_logic.slx';
open_system(mdl);

sim(mdl);
