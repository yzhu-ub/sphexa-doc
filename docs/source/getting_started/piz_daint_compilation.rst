Compile on Piz Daint
====================

CPU Version
-----------

For compilation on Piz Daint, **CPU only**:

.. code-block:: console

    ml HDF5/1.14.2-gompi-2022a-zen2
    ml CMake/3.23.1-GCCcore-11.3.0
    ml CUDA/11.8.0

    mkdir build
    cd build
    cmake <GIT_SOURCE_DIR>
    make -j16 sphexa


CUDA Version
------------

Compilation **with CUDA**:

.. code-block:: console

    module load daint-gpu
    module load CMake/3.22.1
    module load PrgEnv-cray
    module load cdt/22.05           # will load cce/14.0.0
    module load nvhpc-nompi/22.2    # will load nvcc/11.6
    module load gcc/11.2.0
    module load cray-hdf5-parallel

    mkdir build
    cd build
    cmake <GIT_SOURCE_DIR>
    make -j16 sphexa-cuda
