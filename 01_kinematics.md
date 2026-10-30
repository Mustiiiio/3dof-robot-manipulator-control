# Kinematics and Singularity Analysis

## Robot geometry

The supplied report studies a 3-DOF spherical articulated manipulator with `a1 = 0.25 m`, `a2 = 0.15 m`, and `a3 = 0.15 m`. The first joint controls base rotation; the remaining joints determine radial reach and height.

## Forward kinematics

The report obtains the end-effector position from a DH-based homogeneous transform `T03`:

```text
x = cos(q1) * (a2*cos(q2) + a3*cos(q2+q3))
y = sin(q1) * (a2*cos(q2) + a3*cos(q2+q3))
z = a1 + a2*sin(q2) + a3*sin(q2+q3)
```

The actual DH parameter table and transform matrices are not fully reproduced in the report extract; they should be uploaded from the original model or derivation if available.

## Differential kinematics

The **linear** Jacobian is defined as `Jv(q) = ∂p/∂q`, and `p_dot = Jv(q)*q_dot`. Cartesian acceleration follows `p_ddot = Jv(q)*q_ddot + Jv_dot(q,q_dot)*q_dot`.

The determinant stated in the report is:

```text
det(Jv) = -a2*a3*(a2*cos(q2) + a3*cos(q2+q3))*sin(q3)
```

Singularities arise when:

- `sin(q3) = 0` (elbow singularity), or
- `a2*cos(q2) + a3*cos(q2+q3) = 0` (radial/base-axis singularity).

The report uses `q0 = [0.3, 0.5, -0.5]ᵀ rad` and `qf = [1.0, 0.4, 0.7]ᵀ rad` as example endpoint configurations.

## Validation evidence to add

- MATLAB symbolic derivation or script for `T03`, `p(q)`, and `Jv(q)`.
- Numerical finite-difference check of the Jacobian.
- Singularity plot exported from the original report/model.

**Source:** final report, sections 2–3 (pp. 3–5). No standalone MATLAB script was supplied.
