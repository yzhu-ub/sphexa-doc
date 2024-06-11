Welcome to Lumache's documentation!
===================================

**SPH-EXA** is a C++20 simulation code for hydrodynamics simulations (with gravity and other physics), parallelized with MPI, OpenMP, CUDA, and HIP.

**SPH-EXA** is built with *high performance, scalability, portability, and resilience* in mind. Its SPH implementation is based on SPHYNX, ChaNGa, and SPH-flow, three SPH codes selected in the PASC SPH-EXA project to act as parent and reference codes to SPH-EXA.

The performance of standard codes is negatively impacted by factors such as imbalanced multi-scale physics, individual time-stepping, halos exchange, and long-range forces. Therefore, the goal is to extrapolate common basic SPH features, and consolidate them in a fully optimized, Exascale-ready, MPI+X, SPH code: SPH-EXA.

Check out the :doc:`getting_started` section for further information, including
how to :ref:`installation` the project.

.. note::

   This project is under active development.

Contents
--------

.. toctree::

   getting_started
   usage
   api
