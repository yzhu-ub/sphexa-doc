Compile on sciCORE
=====

The following compilation flags are recommended in sciCORE environment for a minimum functionalities:

.. code-block:: console

    ml HDF5/1.14.2-gompi-2022a-zen2
    ml CMake/3.23.1-GCCcore-11.3.0
    ml CUDA/11.8.0

    mkdir build
    cd build
    cmake <GIT_SOURCE_DIR>