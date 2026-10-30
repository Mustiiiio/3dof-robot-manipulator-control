# 3-DOF Spherical Articulated Manipulator — Modeling and Control

**MATLAB / Simulink · Robot Kinematics · Computed Torque Control · Cartesian Tracking · Hybrid Position/Force Control**

> **Project type:** Modeling and simulation (not a physical robot deployment).  
> **Contributors:** Mustafa Mohamed Ahmed Deri and İrfan Gereken.  
> **Academic supervisor:** Assoc. Prof. Kamil Çetin.  
> **Institution:** İzmir Kâtip Çelebi University · May 2026.

## Overview

This project models and controls a **three-degree-of-freedom (3-DOF) spherical articulated robot manipulator** in MATLAB/Simulink. It progresses from Denavit–Hartenberg (DH) kinematics and a nonlinear dynamic model to joint-space and Cartesian control, then introduces contact with a simulated environment for **hybrid position/force control**.

The reported study consists of these stages:

1. **Kinematics and dynamics:** forward kinematics, analytical linear Jacobian, singularity conditions, joint-space inverse dynamics.
2. **Joint-space control:** model-based computed torque control with position and velocity feedback.
3. **Cartesian control:** quintic end-effector reference trajectory and operational-space dynamics.
4. **Hybrid position/force control:** regulate end-effector **x–y position** while tracking **z-axis contact force** against a simulated spring–damper surface.

**Scope:** The original report documents MATLAB/Simulink models and simulation plots. Executable `.slx`/`.m` source files have **not yet been added** to this repository package. Do not interpret the documentation as a reproducible code release until those files are uploaded.

## System parameters

| Parameter | Symbol | Value |
| --- | --- | --- |
| Manipulator mass | `m` | 2.5 kg |
| First geometric parameter | `a1` | 0.25 m |
| Second link length | `a2` | 0.15 m |
| Third link length | `a3` | 0.15 m |
| Gravity | `g` | 9.81 m/s² |

The model uses three joint coordinates `q = [q1, q2, q3]ᵀ` and an end-effector position `p = [x, y, z]ᵀ`.

## Forward kinematics

The position relations reported for the manipulator are:

```text
r = a2*cos(q2) + a3*cos(q2 + q3)
x = cos(q1)*r
y = sin(q1)*r
z = a1 + a2*sin(q2) + a3*sin(q2 + q3)
```

The linear Jacobian is obtained from `Jv(q) = ∂p/∂q` and relates joint velocity to Cartesian velocity: `p_dot = Jv(q) * q_dot`.

The report identifies singular configurations through:

```text
det(Jv) = -a2*a3*(a2*cos(q2) + a3*cos(q2 + q3))*sin(q3)
```

See [Kinematics and singularities](docs/01_kinematics.md).

## Dynamic model

The nonlinear joint-space model is represented as:

```text
tau = M(q)*q_ddot + V(q,q_dot) + G(q) + F(q_dot)
```

where `M` is the inertia matrix, `V` contains Coriolis/centrifugal terms, `G` is gravity, and `F` is friction. A contact force is mapped to joint space using `Jvᵀ * Fe` in the reported simulation.

See [Dynamic model](docs/02_dynamics.md).

## Controllers

| Method | Controlled quantity | Reported implementation |
| --- | --- | --- |
| Inverse dynamics | Joint torques for a prescribed trajectory | MATLAB/Simulink simulation |
| Computed torque control | Joint position/velocity tracking | MATLAB/Simulink simulation |
| Cartesian model-based control | End-effector `x, y, z` position | MATLAB/Simulink simulation |
| Hybrid position/force control | `x, y` position and `z` contact force | MATLAB/Simulink simulation |

The joint-space computed torque controller is:

```text
tau = M(q) * [q_ddot_d + Kv*(q_dot_d - q_dot) + Kp*(q_d - q)]
      + V(q,q_dot) + G(q) + F(q_dot)
```

For hybrid control, the reported direction-selection matrices are:

```text
S_pos = diag([1, 1, 0])
S_for = diag([0, 0, 1])
```

See [Control strategies](docs/03_control_strategies.md).

## Results reported

The report includes Simulink block diagrams and plots for:

- Joint-space inverse-dynamics torques and quintic reference trajectories.
- Joint-space computed-torque tracking and joint error.
- Cartesian end-effector reference tracking and tracking error.
- Hybrid control with contact-force and position-response plots.

For a **5 N desired contact force**, the report's discussion describes an approximately **0.5 N tracking offset (~10%)** in one section; another later plot/text describes the error approaching zero. The original source therefore needs reconciliation before reporting one definitive force-error metric. No new metrics have been calculated for this repository.

See [Results and limitations](docs/04_results_and_limitations.md).

## Repository contents

```text
3dof-robot-manipulator-control/
├── README.md
├── docs/
│   ├── 01_kinematics.md
│   ├── 02_dynamics.md
│   ├── 03_control_strategies.md
│   ├── 04_results_and_limitations.md
│   ├── 05_reproduction_guide.md
│   └── 06_source_review_notes.md
├── models/
│   └── README.md
├── results/
│   └── README.md
└── .gitignore
```

## Reproduction status

The documentation is based on the academic final report. **Model files, controller parameter sets, MATLAB version/toolbox details, and raw simulation outputs must be provided before another researcher can reproduce the results.** A practical upload checklist is provided in the [reproduction guide](docs/05_reproduction_guide.md).

## Attribution

This was a **collaborative academic project** by **Mustafa Mohamed Ahmed Deri and İrfan Gereken**, supervised by **Assoc. Prof. Kamil Çetin**. The individual contributions of each student were not separated in the supplied report, so this repository does not assign specific modules to either contributor.

## Contact

- [Mustafa Deri on GitHub](https://github.com/Mustiiiio)
- [LinkedIn](https://www.linkedin.com/in/mustafa-deri-78142125a/)

## Source

Prepared from *Modeling and Control of a 3-DOF Spherical Articulated Manipulator — Final Report* (20 May 2026). The report itself is not included in this starter package because it contains student identification details and collaborative academic material; review with the co-author before publishing it.
