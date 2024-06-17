Built-in Initial Conditions
=====

The SPH-EXA framework has implemented a few initial conditions, for testing purposes and also showcasing. Users can load the initial conditions by specifying their names when executing with command-line like below:

.. code-block:: console

    --init <name of built-in initial conditions or initial condition file path>
  
Implemented initial conditions
------------------------------

Sedov: spherical blast wave
^^^^^

`--init sedov`

Spatial boundary:

x: [0, 1]

y: [0, 1]

z: [0, 1]

Spherical Implosion
^^^^^

`--init noh`

Spatial boundary:

x: [0, 1]

y: [0, 1]

z: [0, 1]


Evrard: gravitational collapse of an isothermal cloud
^^^^^

`--init evrard`

Spatial boundary:

x: [0, 1]

y: [0, 1]

z: [0, 1]


Turbulence: subsonic turbulence in a box
^^^^^

`--init turbulence`

Spatial boundary:

x: [-0.5, 0.5]

y: [-0.5, 0.5]

z: [-0.5, 0.5]



Kelvin-Helmholtz: 
^^^^^

`--init kelvin-helmholtz`

Spatial boundary:

x: [-0.5, 0.5]

y: [-0.5, 0.5]

z: [-0.5, 0.5]


