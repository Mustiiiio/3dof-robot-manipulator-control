# Control Strategies

## 1. Joint-space inverse dynamics

A prescribed joint trajectory provides `q_d`, `q_dot_d`, and `q_ddot_d`. The nonlinear model computes feedforward joint torques. This is used as an initial verification of the dynamic model, not as proof of disturbance rejection.

## 2. Joint-space computed torque control

The report uses a model-based PD structure:

```text
e_q = q_d - q
edot_q = q_dot_d - q_dot

tau = M(q) * (q_ddot_d + Kv*edot_q + Kp*e_q)
      + V(q,q_dot) + G(q) + F(q_dot)
```

`Kp` and `Kv` are controller gains. Their numerical values are not included in the supplied report and should be extracted from the actual Simulink model.

## 3. Cartesian model-based control

A quintic Cartesian reference trajectory is generated from the forward-kinematics positions of the selected initial and final joint configurations. The report defines Cartesian position and velocity errors and uses a model-based acceleration command:

```text
a_x = x_ddot_ref + Kv*(x_dot_ref - x_dot) + Kp*(x_ref - x)
```

The report expresses the operational-space model as:

```text
Mx = J^(-T) * M * J^(-1)
Vx = J^(-T) * (V - M*J^(-1)*J_dot*q_dot)
Gx = J^(-T) * G
Fx = Mx*a_x + Vx + Gx
tau = J^T * Fx
```

It reports using a **damped Jacobian inverse** near singular configurations rather than a direct inverse. The damping parameter and implementation should be documented from the original model.

## 4. Hybrid position/force control

The final stage combines:

- Position control in the Cartesian `x` and `y` directions.
- Contact-force control along the `z` direction.

Selection matrices:

```text
S_pos = diag([1,1,0])
S_for = diag([0,0,1])
```

The environment is a simulated spring–damper surface. The report models the normal force as:

```text
Fe = k*(z_surface - z) - b*z_dot,  if z < z_surface
Fe = 0,                            otherwise
```

The report also describes force-direction sign handling and torque saturation. For a faithful reproduction, retrieve the actual block implementation and coefficients; do not substitute a generic controller without labeling it as a new implementation.

**Source:** final report, sections 5–8 (pp. 7–10).
