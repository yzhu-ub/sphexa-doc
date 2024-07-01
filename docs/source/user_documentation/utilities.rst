Utilities
=====

With some third-party tools SPH-EXA can have extra features which might be very useful during simulation. Here we introduce some important integrations that user can benefit from.

In-Situ data analysis
-----


Compilation on LUMI with Ascent

.. note::

    Please make sure you have an up-to-date installation of CMake (>= v3.24) in user directory that you can execute from. 


.. code-block:: console

    export SPACK_USER_PREFIX=/pfs/lustrep1/scratch/project_465000808/
    export MPICH_GPU_SUPPORT_ENABLED=1
    module load CrayEnv buildtools/22.08 craype-accel-amd-gfx90a rocm cray-hdf5-parallel
    module load spack/23.09
    . /pfs/lustrep3/appl/lumi/spack/23.09/0.21.0-user/share/spack/setup-env.sh

    spack load ascent

Build SPH-EXA with in-situ data support (with GPU code):

.. code-block:: console
    cd ~
    git clone https://github.com/unibas-dmi-hpc/SPH-EXA.git
    cd SPH-EXA
    git checkout insitu3 # The latest branch that integrates Ascent support
    git submodule update --init --recursive
    hipify-perl -inplace `find -name *.cu -o -name *.cuh` && find -name *.prehip -delete
    cd ../
    mkdir compbuild
    cd compbuild

    # Please check your cmake version before continuing! It has to be later than v3.24.
    cmake -DCMAKE_CXX_COMPILER=CC -DCMAKE_HIP_ARCHITECTURES=gfx90a -DCMAKE_HIP_COMPILER=CC -DCMAKE_HIP_COMPILER_FORCED=ON -DGPU_DIRECT=OFF -DINSITU=Ascent -DAscent_DIR=$(spack location --install-dir ascent)/lib/cmake/ascent -S ../SPH-EXA

Then tweak the flags a bit:

.. code-block:: console
    vi main/src/sphexa/CMakeFiles/sphexa-hip.dir/flags.make

And remove the flag `-fcompare-debug-second` from `CXX_FLAGS`. Save. Then,

.. code-block:: console
    make -j16 sphexa-hip


SPH-EXA has a few sample scripts for visualizing typical scenarios. To test them, first copy all contents from `SPH-EXA/scripts/ascent` into the same directory as `sphexa-hip`. 

Then, in file `ascent_actions.yaml`, change line 9 and point it to the script you would like to execute.

Submit the job
^^^^^^^^^^^^^^

.. note::

    Only the propagators with visualization infrastructure integrated, i.e. `insituvis_ve` and `insituvis`, can be executed with in-situ data analysis pipeline.

When submitting a simulation job for visualization, please note the possible fields to be exported. They should be specified with flag `-v`.

Examples

In-situ density PDF for a 400^3 turbulence simulation until physical time t=0.251s:

.. code-block:: yaml
        actions_file: "testcases/turbulence/pdf.yaml"

.. code-block:: console
    sphexa-hip --init <init_data_path> --prop insituvis_ve -s 0.251 -n 400 -v x,y,z,vx,vy,vz,rho










