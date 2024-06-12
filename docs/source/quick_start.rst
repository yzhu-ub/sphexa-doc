Quick Started
=============

Compile and run SPH-EXA
-----------------------

To run SPH-EXA, the following software requirements have to be met:

* A C++ 20 Compiler (gcc >= 11, clang >= 12) with OpenMP support
* CMake >= 3.22


Download the latest SPH-EXA code:

.. code-block:: console

    git clone https://github.com/unibas-dmi-hpc/SPH-EXA.git
    cd SPH-EXA && git checkout develop

Then build it with minimal CMake options:

.. code-block:: console

    mkdir build
    cd build
    cmake -S ../
    make sphexa

The commands above will build the CPU version of SPH-EXA with OpenMP enabled. Executable is located in: `SPH-EXA/build/main/src/sphexa/sphexa`.

To run a testcase with it:

.. code-block:: console

    ./main/src/sphexa/sphexa --init sedov -n 50 -s 10 -w 10

The line above runs a testcase **Sedov blastwave** with 125000(50^3) particles for 10 timesteps. It will also output a checkpoint at the 10th timestep. For each timestep, you will see output similar to:

.. code-block:: console

    # Visualization: 0.00756577s
    # domain::sync: 0.324575s
    # FindNeighbors: 0.509515s
    # XMass: 0.0790799s
    # mpi::synchronizeHalos: 0.000126762s
    # Normalization & Gradh: 0.0877948s
    # EquationOfState: 0.00152708s
    # mpi::synchronizeHalos: 5.3358e-05s
    # IadVelocityDivCurl: 0.338403s
    # mpi::synchronizeHalos: 4.8261e-05s
    # AVswitches: 0.092626s
    # mpi::synchronizeHalos: 0.000107416s
    # MomentumAndEnergy: 0.194415s
    # Timestep: 5.1612e-05s
    # UpdateQuantities: 0.0226838s
    ### Check ### Global Tree Nodes: 512, Particles: 125000, Halos: 0
    ### Check ### Computational domain: -0.5 0.5 -0.5 0.5 -0.5 0.5
    ### Check ### Total Neighbors: 11625000, Avg neighbor count per particle: 93
    ### Check ### Total time: 2.31e-06, current time-step: 1.21e-06
    ### Check ### Total energy: 1, (internal: 1, kinetic: 3.12759e-08, gravitational: 0)
    ### Check ### Focus Tree Nodes: 4096, maxDepth 4
    === Total time for iteration(2) 1.65101s

This is the basics of SPH-EXA usage. For more use cases and info, see the next pages.
