# Simulation Results and Limitations

## Evidence described in the report

| Experiment | Reported outputs | Interpretation in the report |
| --- | --- | --- |
| Joint-space inverse dynamics | Joint torque histories and prescribed joint trajectories | Shoulder and elbow torques are larger than the base torque due to gravity |
| Computed torque control | Joint torques, tracking errors, measured vs desired angles | Tracking errors approach zero |
| Cartesian model-based control | Joint torques, Cartesian position errors, measured vs desired end-effector positions | End-effector tracks the Cartesian reference |
| Hybrid position/force control | Joint torques, x–y tracking errors, position and force plots | x–y position regulation while controlling z-axis contact force |

These are **report descriptions**, not newly computed performance measurements. Figures and raw `.mat` outputs are not included in this starter repository.

## Contact force result: source inconsistency

In the report's contact-environment discussion (p. 10), the force tracking error is described as approximately `-0.5 N` for a `5 N` reference (about 10%). In the later results discussion (p. 18), a similar offset is described. However, the plots and adjacent text on p. 19 describe the force error decreasing toward zero.

**Publication action:** Reopen the actual model/results and measure steady-state force error from the same run before stating a definitive numeric outcome. Until then, describe the outcome as **force tracking demonstrated in simulation, with a discrepancy in the reported steady-state error**.

## Other limitations

- Simulation-only; no real manipulator hardware testing is documented.
- Source code and model files are not yet uploaded.
- Exact controller gains, contact stiffness/damping, friction coefficients, solver settings, and MATLAB version are not specified.
- The report refers to a *quintic* trajectory but one caption describes a *quadratic* profile; verify the trajectory generator before making a reproducibility claim.
- Several figure numbers are reused in the original report; use unique filenames/captions when exporting figures.

## Figures to export

Suggested file names for genuine report figures:

```text
results/figures/01_singularity_map.png
results/figures/02_joint_torque_inverse_dynamics.png
results/figures/03_joint_trajectory.png
results/figures/04_computed_torque_tracking.png
results/figures/05_cartesian_tracking.png
results/figures/06_hybrid_position_tracking.png
results/figures/07_contact_force_tracking.png
```

Only add files when exported from the original work; do not use generated example plots as experimental evidence.

**Source:** final report, results section (pp. 10–20).
