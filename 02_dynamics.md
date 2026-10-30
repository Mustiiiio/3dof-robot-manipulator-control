# Manipulator Dynamic Model

## Governing equation

The report represents the three-joint nonlinear dynamics as:

```text
tau = M(q)*q_ddot + V(q,q_dot) + G(q) + F(q_dot)
```

- `tau`: vector of applied joint torques, N·m.
- `M(q)`: joint-space inertia matrix.
- `V(q,q_dot)`: Coriolis and centrifugal terms.
- `G(q)`: gravitational torques.
- `F(q_dot)`: friction torques.

The inertia matrix is structured as:

```text
M(q) = [M11,   0,   0;
           0, M22, M23;
           0, M23, M33]
```

The report supplies component-wise expressions for `M`, `V`, and `G` in sections 4 and the subsequent page. Those expressions should be transferred directly from the verified MATLAB source rather than retyped into runnable code without checking notation and dimensional consistency.

## Friction model

The report introduces viscous and smooth Coulomb-like friction:

```text
F(q_dot) = Fv*q_dot + Fc*tanh(alpha*q_dot)
```

The coefficient values (`Fv`, `Fc`, `alpha`) are **not established in the supplied report** and must be documented from the actual simulation.

## Plant equations

Without contact:

```text
q_ddot = M(q)^(-1) * (tau - V - G - F)
```

With environment contact, the report writes:

```text
q_ddot = M(q)^(-1) * (tau + Jv(q)^T*Fe - V - G - F)
```

The contact-force sign convention must be preserved consistently when porting the Simulink blocks.

## Verification to add

1. Inspect `M(q)` for symmetry and positive definiteness over the operating range.
2. Check the units of joint torque, link geometry, and contact force.
3. Verify inverse dynamics against the plant model.
4. Record exact model coefficients and MATLAB/Simulink version.

**Source:** final report, section 4 (pp. 5–6).
