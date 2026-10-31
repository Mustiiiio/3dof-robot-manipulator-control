# Reproduction Guide — Pending Source Upload

This project currently contains **documentation only**. The academic report includes model block diagrams but does not supply executable `.slx` and `.m` files. The following steps are a checklist for preparing a reproducible release, **not** instructions that have already been verified.

## Files to obtain from the original project

- [ ] Simulink model for joint-space inverse dynamics.
- [ ] Simulink model for computed torque control.
- [ ] Simulink model for Cartesian control.
- [ ] Simulink model for hybrid position/force control.
- [ ] MATLAB initialization scripts defining masses, lengths, gains, and contact parameters.
- [ ] MATLAB/Simulink version and required toolboxes.
- [ ] Solver settings, time steps, stop times, and initial conditions.
- [ ] Exported original figures and raw simulation results (`.mat` where appropriate).
- [ ] Co-author permission/attribution check before publishing shared academic code and report.

## Proposed source organization

```text
models/
  joint_inverse_dynamics.slx
  computed_torque_control.slx
  cartesian_control.slx
  hybrid_position_force.slx
scripts/
  init_parameters.m
  run_all.m
results/
  figures/
  data/
```

**These filenames are suggestions only** and are not present in the starter package. Preserve the original project filenames when possible, then document what each one does.

## Once files are available

1. Open MATLAB in a clean working directory.
2. Run the project's actual parameter-initialization script.
3. Open each model and verify the signal interfaces.
4. Reproduce the report's starting/ending joint configurations and reference trajectories.
5. Run each model with the recorded solver configuration.
6. Export results and compare them against the original report's plots.
7. Record numerical tracking metrics directly from simulation output.

Do not claim a successful reproduction until these steps have been executed.
