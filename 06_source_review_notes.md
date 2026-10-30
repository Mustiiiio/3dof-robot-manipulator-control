# Source Review Notes Before Public Release

The documentation in this repository is derived from the academic report *Modeling and Control of a 3-DOF Spherical Articulated Manipulator* (submitted 20 May 2026).

## Provenance and credit

The report names **Mustafa Mohamed Ahmed Deri** and **İrfan Gereken** as students and **Doç. Dr. Kamil Çetin** as supervisor. It does not assign individual modules or specific contributions to each student. Keep both students credited until contribution details are confirmed.

## Points needing verification against original models

1. **Contact-force tracking:** text describing ~0.5 N error and figures describing near-zero error appear in different parts of the report.
2. **Trajectory naming:** the text describes quintic trajectories; one caption refers to a quadratic trajectory.
3. **Figure references:** figure numbers are reused in the report; renumber or use descriptive filenames.
4. **Exact parameterization:** controller gains, friction parameters, environment stiffness/damping, solver settings, and version information are missing from the report.
5. **Model equations:** verify all dynamic terms and signs directly against the original MATLAB/Simulink code before transcribing them into executable files.
6. **Privacy:** do not publish student numbers, personal identification details, or the unredacted academic cover page by default.
7. **Publication rights:** obtain agreement from the co-author before publishing jointly authored code, report pages, or figures. Confirm any course/institutional restrictions.

This document records source ambiguities rather than silently resolving them.
