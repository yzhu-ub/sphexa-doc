Command Line Options
=====

Overview
--------

.. note::

    This page only lists the options for minimal functionalities. For optional functionalities that requires a third-party dependency, please check corresponding pages for details. 

The main `sphexa` (and `sphexa-cuda`, if GPUs are available) application can either start a simulation by reading initial conditions from a file, or generate an initial configuration for a named test case. 


Self gravity
^^^^^^^^^^^^

Self-gravity will be activated automatically based on named test-case choice or if the HDF5 initial configuration file has an HDF5 attribute with a non-zero value for the gravitational constant.


Basic command-line options
--------------------------

In latest release, the following command-line options are available:

Arguments:

* `--init <name of built-in initial conditions or initial condition file path>`
  
  provide an HDF5 file with initial conditions, or use one of the built-in initial conditions. See :doc:`user_documentation/builtin_initial_conditions` for available initial conditions. 

* `--glass <glass file path>`
  template glass block for IC generation avaiable from DOI

* `-n NUM`
  Run the simulation with NUM^3 (NUM to the cube) number of particles (for named test cases). 
  
  .. note::

    The number of actual particles might vary with initial conditions.

* `-s NUM`
  Run the simulation with NUM of iterations (time-steps) if NUM is integer. Run until the specified physical time if NUM is real.

* `-w NUM`
  Dump particle data every NUM iterations (time-steps) if NUM is integer. Dump data at the specified physical time if NUM is real.

* `-f FIELDS`
  Comma separated list of particle fields for file output dumps. See a list of common ouput fields below.

* `--duration NUM`
  Run the simulation for certain wallclock time, specified in seconds (integer). Dump a checkpoint at the end of the duration.

* `--quiet`
  Don't print any output to stdout


