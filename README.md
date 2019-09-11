# HArDCore

HArDCore (Hybrid Arbitrary Degree::Core) is a set of two projects providing C++ libraries to implement 2D and 3D schemes, on general polytopal meshes, with main unknowns being polynomials in the mesh elements and on the mesh faces (hybrid methods).

The library was designed with the Hybrid High-Order method in mind (see the book https://hal.archives-ouvertes.fr/hal-02151813), and several HHO methods are already implemented in this framework, but the tools provided in this library are useful for a range of hybrid methods.

This page is merely a landing page to redirect you to the 2D or 3D codes:

**HArDCore2D**

*sources*: https://github.com/jdroniou/HArDCore2D<br>
*documentation*: https://jdroniou.github.io/HArDCore2D

**HArDCore3D**

*Coming soon... (hopefully by mid-July). HArDCore3D is built to follow HArDCore2D, so that adapting a code from 2D to 3D only takes a minimal amount of time (it merely consist in changing some "edge" in the code into "faces", etc.)*


Although these 2D and 3D libraries are separate, they have been designed for an easy adaptation of implementations from one to the other. Typically, to adapt the implementation of a numerical methods from 2D to 3D, one has to perform the following changes in the source files:

- 2d (e.g. in "Vector2d"): change into 3d
- edge (Edge): change into face (Face).
- .x() (and .x): correspond to functions of two variables (e.g. f(v.x(), v.y()) if v is Eigen::Vector2d) and quadrature nodes
(q.x, q.y), to which a third variable .z should be added (into f(v.x(), v.y(), v.z()), etc.)

Experience with the schemes currently implemented in HArDCore2D and HArDCore3D show that 30'-45' are sufficient to do these changes and test the resulting code.

