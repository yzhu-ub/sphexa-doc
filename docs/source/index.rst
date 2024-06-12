Welcome to SPH-EXA!
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

Ascent Documentation
======================

.. toctree::
   :maxdepth: 1
   :hidden:

   QuickStart

.. toctree::
   :caption: Tutorial
   :maxdepth: 1
   :hidden:

   getting_started/overview


.. toctree::
   :caption: User Documentation
   :maxdepth: 1
   :hidden:

   getting_started/overview

.. toctree::

   quick_start


.. toctree::
   :caption: Getting Started
   :maxdepth: 1
   :hidden:

   getting_started/overview
   getting_started/local_compilation
   getting_started/scicore_compilation
   getting_started/piz_daint_compilation
   getting_started/lumi_compilation


.. toctree::
   :caption: Tutorial
   :maxdepth: 1
   :hidden:

   tutorial


.. toctree::
   :caption: User Documentation
   :maxdepth: 1
   :hidden:

   user_documentation/command_line_options
   user_documentation/builtin_initial_conditions
   user_documentation/propagators
   user_documentation/io_interface
   user_documentation/utilities


.. toctree::
   :caption: Developer Documentation
   :maxdepth: 1
   :hidden:

   architecture_overview
   writing_test_cases


.. toctree::
   :caption: About
   :maxdepth: 1
   :hidden:
   
   about
