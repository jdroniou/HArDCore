# HArDCore

HArDCore (Hybrid Arbitrary Degree::Core) is a set of two projects providing C++ libraries to implement 2D and 3D schemes, on general polytopal meshes, with main unknowns being polynomials in the mesh elements, on the mesh faces and on the mesh edges (hybrid methods).

The library was designed with the Hybrid High-Order method in mind (see the book https://hal.archives-ouvertes.fr/hal-02151813), and several HHO methods are already implemented in this framework, but the tools provided in this library are useful for a range of numerical methods.

This page is merely a landing page to redirect you to the 2D or 3D codes:

**HArDCore2D**

*sources*: https://github.com/jdroniou/HArDCore2D-release/<br>
*documentation* (latest release only): https://jdroniou.github.io/HArDCore2D-release/

**HArDCore3D**

*sources*: https://github.com/jdroniou/HArDCore3D-release/<br>
*documentation* (latest release only): https://jdroniou.github.io/HArDCore3D-release/


Although these 2D and 3D libraries are separate, they have been designed for a straightforward adaptation of implementations from one to the other. The following rules should be used when implementing a scheme in 2D or 3D:

- Whenever the space dimension must be accessed, do not use '2' or '3' in hard by rather the `dimspace` parameter from `basis.hpp` or the `dim()` method in the class `Mesh`.
- Similarly, when needing vectors in 2D or 3D, do not use `Vector2d` or `Vector3d` from Eigen, but rather the generic type `VectorRd` from `basis.hpp`.
- The functions depending on 2 or 3 variables should not actually be of several variables, as in `std::function<double(double,double)>`, but rather functions depending on one vector as in `std::function<double(VectorRd)>`.
- Quadrature nodes should be accessed via the `.vector()` method


If these rules are applied, and if the scheme's mathematical description is independent of the spatial dimension, then transforming a 2D implementation into a 3D implementation (and similarly in the other direction) essentially consists in:

- Changing the namespace HArDCore2D into HArDCore3D.
- Adapting the executable parameters and mesh loading procedures (use one of the examples in the library of the corresponding dimension, e.g. `HHO_diffusion`).
- Changing all occurences of `edge` into `face`, and `Edge` into `Face`.
- Function for visualisation (creation of a vtk/vtu file): copy from one of the existing 3D examples
- Optionally, some introduced variable names (e.g. `area`, `E` for an edge, etc.) could be changed to reflect the 3D version they now represent, but that's not mandatory.

This transformation was done for several schemes currently implemented in HArDCore2D and HArDCore3D, and each one took approximatively 20 minutes (including tests of the resulting code).

