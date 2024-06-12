Compilation Overview
====================

.. note::

    This section only lists the compilation steps for minimal functionalities. Regarding functionalities that requires a third-party dependency, please check ::doc:`user_documentation` for details. 

Compiling SPH-EXA is similar to compiling any other C++ projects on Linux/Unix machines. SPH-EXA utilizes the latest C++ features, requiring C++ 20 for a complete build of the CPU code. For its CUDA part, the minimum supported CUDA version is CUDA 11.2 with a C++17 host compiler, e.g. GCC 9.3.0.

For ease of use, the recommended minimum version of CUDA is 11.4.1 which supports GCC 11, providing both the required C++20 support and bug-free CUDA host compilation. 

.. note::

    CUDA/11.3.1 seems to have solved the compatibility issues with GCC 10.3.0.

For basic checkpointing, it is also recommended to have HDF5 installed in your building environment. When running CMake, make sure that `HDF5_DIR` is pointed to the correct path.

To summarize, the following software requirements have to be met:

* A C++ 20 Compiler (gcc >= 11, clang >= 12) with OpenMP support
* CMake >= 3.22

The following are recommended:

* CUDA >= 11.4.1
* HDF5 >= 1.8.0