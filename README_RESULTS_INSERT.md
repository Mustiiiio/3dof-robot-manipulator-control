## Simulation Results

The project evaluates three model-based control strategies using MATLAB/Simulink. The figures below are taken from the original simulation report; they are not physical robot measurements.

### Joint-Space Computed Torque Control
![Joint-space control model](results/figures/joint_space_simulink.png)
![Joint-space desired vs actual](results/figures/joint_space_reference_vs_actual.png)
![Joint-space tracking error](results/figures/joint_space_tracking_error.png)

### Cartesian Model-Based Control
![Cartesian control model](results/figures/cartesian_simulink.png)
![Cartesian desired vs actual](results/figures/cartesian_reference_vs_actual.png)
![Cartesian tracking error](results/figures/cartesian_tracking_error.png)

### Hybrid Position/Force Control
![Hybrid control model](results/figures/hybrid_simulink.png)
![Hybrid contact force tracking](results/figures/hybrid_force_tracking.png)
![Hybrid force error](results/figures/hybrid_force_error.png)

The original force-response plot approaches the 5 N reference. Because the report gives inconsistent descriptions of the final force error, a numerical steady-state error is not claimed here. See [all results, actuator torque plots and detailed captions](results/RESULTS.md).
