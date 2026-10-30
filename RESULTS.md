# Simulation Results — 3-DOF Manipulator

These figures were extracted **directly from the original project report**. They document MATLAB/Simulink simulations, not physical robot experiments. The original figure numbering in the report contains duplicates, so this gallery uses descriptive filenames instead.

## 1. Joint-Space Computed Torque Control

### Simulink architecture
![Joint-space controller architecture](figures/joint_space_simulink.png)

*Joint-space computed torque controller integrating PD tracking feedback with inverse dynamics.*

### Reference vs. actual joint angles
![Joint tracking](figures/joint_space_reference_vs_actual.png)

*Desired and simulated joint-angle trajectories for the waist, shoulder, and elbow. The curves are visually close in the plotted test.*

### Joint tracking error
![Joint tracking error](figures/joint_space_tracking_error.png)

*Joint position tracking errors during the simulation. Numerical performance metrics are not reported because the raw logged data have not been verified.*

### Actuator torques
![Joint torques](figures/joint_space_torques.png)

*Computed actuator torque commands for the three joints.*

## 2. Cartesian Model-Based Control

### Simulink architecture
![Cartesian control architecture](figures/cartesian_simulink.png)

*Cartesian controller with kinematics and operational-space model-based feedback.*

### Desired vs. actual end-effector position
![Cartesian reference vs actual](figures/cartesian_reference_vs_actual.png)

*End-effector x, y, and z positions in the simulated Cartesian tracking task.*

### Cartesian position tracking error
![Cartesian error](figures/cartesian_tracking_error.png)

*Position tracking error in the three Cartesian directions. Refer to the axes and curves when evaluating convergence.*

### Actuator torques
![Cartesian torques](figures/cartesian_torques.png)

*Joint torque outputs under Cartesian model-based control.*

## 3. Hybrid Position/Force Control

### Simulink architecture
![Hybrid control architecture](figures/hybrid_simulink.png)

*Hybrid position/force controller with contact environment dynamics. The design targets position control in x and y and contact-force control in z.*

### Desired vs. actual Cartesian position
![Hybrid position](figures/hybrid_reference_vs_actual.png)

*Simulated end-effector position with the contact constraint active. Z-position is not required to follow a free-space reference during force regulation.*

### Cartesian position error
![Hybrid position error](figures/hybrid_position_error.png)

*Original plotted Cartesian position errors. Interpret the z error separately from x/y because the z direction is force-controlled.*

### Contact force tracking
![Hybrid force tracking](figures/hybrid_force_tracking.png)

*Desired contact force (5 N) and simulated environment force in the z direction. The original graph visually approaches the reference.*

### Contact force error
![Hybrid force error](figures/hybrid_force_error.png)

*Original force-error response. The report also describes an approximately 0.5 N offset in a separate passage; these statements need reconciliation from the logged simulation signals before quoting a numerical steady-state error.*

### Joint torques
![Hybrid torques](figures/hybrid_torques.png)

*Joint torque commands during hybrid position/force control.*

## Reproducibility and limitations

- Figures are extracted from the submitted project report, not re-generated from simulation logs.
- MATLAB/Simulink execution and numerical accuracy have not been independently verified.
- Some figure numbers and written conclusions in the report are inconsistent. The original images have not been edited to conceal those issues.
- This package intentionally excludes `.m` and `.slx` source files, which will be reviewed and published separately.
