Utilities
=====

With certain third-party tools, SPH-EXA can extend its functionality with additional features during simulations. Below are several key integrations that can be utilized for enhanced capabilities.

In-Situ data analysis
-----


Compilation on LUMI with Ascent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Set up environment

.. note::

    Please ensure that you have a recent installation of CMake (version 3.24 or higher) that is accessible for execution.


.. code-block:: console

    export SPACK_USER_PREFIX=/pfs/lustrep1/scratch/project_465000808/
    export MPICH_GPU_SUPPORT_ENABLED=1
    module load CrayEnv buildtools/22.08 craype-accel-amd-gfx90a rocm cray-hdf5-parallel
    module load spack/23.09
    . /pfs/lustrep3/appl/lumi/spack/23.09/0.21.0-user/share/spack/setup-env.sh

    spack load ascent

- Build SPH-EXA with in-situ data support (with GPU code)

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

Remove the flag `-fcompare-debug-second` from `CXX_FLAGS`, Save. Then,

.. code-block:: console

    make -j16 sphexa-hip

SPH-EXA provides sample scripts designed for visualizing common scenarios. To test these scripts, start by copying all contents from `SPH-EXA/scripts/ascent` into the directory where `sphexa-hip` is located.

Next, locate the file named `ascent_actions.yaml` and modify line 9 to specify the script you wish to execute.


Submit the job
^^^^^^^^^^^^^^

.. note::

    Only the propagators with visualization infrastructure integrated, i.e. `insituvis_ve` and `insituvis`, can be executed with in-situ data analysis pipeline.

When submitting a simulation job for in-situ visualization, please ensure to specify the fields being used during visualization using the -v flag.

Examples

In-situ density PDF for a 400^3 turbulence simulation until physical time t=0.251s:

.. code-block:: yaml

    actions_file: "testcases/turbulence/pdf.yaml"

.. code-block:: console

    sphexa-hip --init <init_data_path> --prop insituvis_ve -s 0.251 -n 400 -v x,y,z,vx,vy,vz,rho










