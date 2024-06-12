Compile on LUMI
=====

For compilation on LUMI, we use HIP to convert CUDA code:

.. code-block:: console

    module load CrayEnv
    module load buildtools/22.08
    module load craype-accel-amd-gfx90a rocm cray-hdf5-parallel

    cd <GIT_SOURCE_DIR>; hipify-perl -inplace `find -name *.cu -o -name *.cuh` && find -name *.prehip -delete
    
    cmake -DCMAKE_CXX_COMPILER=CC -DCMAKE_HIP_ARCHITECTURES=gfx90a -DCMAKE_HIP_COMPILER=CC -DCMAKE_HIP_COMPILER_FORCED=ON -DGPU_DIRECT=<ON/OFF> -S <GIT_SOURCE_DIR>
