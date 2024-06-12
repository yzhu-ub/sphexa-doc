Compile on Piz Daint
====================

CPU Version
-----------

For compilation on Piz Daint, **CPU only**:

.. code-block:: console

    module load PrgEnv-cray
    module load cdt/22.05 # will load cce/14.0.0
    export PATH=/opt/nvidia/hpc_sdk/Linux_x86_64/22.2/cuda/11.6/bin:$PATH
    module load gcc/11.2.0
    module load cray-hdf5-parallel
    export LD_LIBRARY_PATH=$CRAY_LD_LIBRARY_PATH:LD_LIBRARY_PATH

    mkdir build
    cd build
    CC=cc CXX=CC cmake -DCMAKE_CUDA_ARCHITECTURES=60 -S <GIT_SOURCE_DIR>
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
    CC=cc CXX=CC cmake -DCMAKE_CUDA_ARCHITECTURES=60 -S <GIT_SOURCE_DIR>
    make -j16 sphexa-cuda
