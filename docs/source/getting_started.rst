Getting Started
=====

.. _installation:

Compile and run SPHEXA locally
------------

.. code-block:: console

   mkdir build
   cd build
   cmake <GIT_SOURCE_DIR>

Compilation on sciCORE
------------

.. code-block:: console

   ml HDF5/1.14.2-gompi-2022a-zen2
   ml CMake/3.23.1-GCCcore-11.3.0
   ml CUDA/11.8.0

   mkdir build
   cd build
   cmake <GIT_SOURCE_DIR>

Compilation on Piz Daint
------------

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

   # C-compiler is needed for hdf5 detection
   CC=cc CXX=CC cmake -DCMAKE_CUDA_ARCHITECTURES=60 -S <GIT_SOURCE_DIR>


Compilation on LUMI
------------

.. code-block:: console

   module load CrayEnv buildtools/22.08 craype-accel-amd-gfx90a rocm cray-hdf5-parallel
   cd <GIT_SOURCE_DIR>; hipify-perl -inplace `find -name *.cu -o -name *.cuh` && find -name *.prehip -delete
   cmake -DCMAKE_CXX_COMPILER=CC -DCMAKE_HIP_ARCHITECTURES=gfx90a -DCMAKE_HIP_COMPILER=CC -DCMAKE_HIP_COMPILER_FORCED=ON -DGPU_DIRECT=<ON/OFF> -S <GIT_SOURCE_DIR>

.. _installation_spack:

Installation using Spack
------------

Some text

.. code-block:: console

   some text


