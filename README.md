# HArDCore

HArDCore (Hybrid Arbitrary Degree::Core) is a set of two projects providing C++ libraries to implement 2D and 3D schemes, on general polytopal meshes, with main unknowns being polynomials in the mesh elements and on the mesh faces (hybrid methods).

The library was designed with the Hybrid High-Order method in mind (see the book https://hal.archives-ouvertes.fr/hal-02151813), and several HHO methods are already implemented in this framework, but the tools provided in this library are useful for a range of hybrid methods.

This page is merely a landing page to redirect you to the 2D or 3D codes:

**HArDCore2D**

*sources*: https://github.com/jdroniou/HArDCore2D<br>
*documentation*: https://jdroniou.github.io/HArDCore2D

**HArDCore3D**

*sources*: https://github.com/jdroniou/HArDCore3D<br>
*documentation*: https://jdroniou.github.io/HArDCore3D


Although these 2D and 3D libraries are separate, they have been designed for an easy adaptation of implementations from one to the other. Typically, if a 2D version of a numerical method is available in which the dimension was not hardcoded as `2` but using the `dim()` method of the Mesh class, adapting it to 3D mostly consists in performing the following changes in the source files:

- Executable parameters and mesh loading procedures have to be copied from an existing 3D example, and replace the equivalent 2D version
- 2d/2D (e.g. in "Vector2d" or "HArDCore2D"): change into 3d/3D
- edge (Edge): change into face (Face).
- `std::function<double(double,double)>`: change into `std::function<double(double,double,double)>` (and similar)
- .x() (and .x): correspond to functions of two variables (e.g. f(v.x(), v.y()) if v is Eigen::Vector2d) and quadrature nodes
(q.x, q.y), to which a third variable .z should be added (into f(v.x(), v.y(), v.z()), etc.)
- lambda functions: adapt to 3 variables
- Function for visualisation (creation of a vtk/vtu file): copy from one of the existing 3D examples
- Optionally, some variable names (e.g. `area`, etc.) could be changed to reflect the 3D version they now represent, but that's not mandatory.

Experience with the schemes currently implemented in HArDCore2D and HArDCore3D show that 30'-45' are sufficient to do these changes and test the resulting code.

