# Introduction

In most cases where DEM is used, it is necessary to carry out some averaging of the data to a more representative scale of what is required.
As such it is quite common for spatial averaging, temporal averaging or both to be applied to the DEM data.
To aid the process, [Particle-Analytics](http://particle-analytics.com/) has been developed to support many codes such as EDEM, PFC, DEMPack and LAMMPS and provides a simple interface for the averaging
process for the large datasets that DEM simulations produce.
The toolbox provides both a coarse graining method for projecting the results on to a continuum field and a binning method.
Some of the results are shown in Figure 1.1.
The coarse-grained density ρ is provided by equation:

![](img/Eqn01.png)

where **r** is a point in space where the values are to be evaluated, **r**(t)_i is the vector of the centres of mass of the particles at a given timestep t,
and φ is the coarse graining function which is subject to the condition of its integral over space being unity.

The coarse-grained velocity V is provided from equation 

![](img/Eqn02.png)

where **p** is the coarse-grained momentum density.

The stress tensor is given by equation

![](img/Eqn03.png)

where *f_ijα* is the interaction force between two particles, *r_ijβ* is the branch vector, *s* is the integral of the
branch vector and *v'* is the fluctuating velocity of the particle.

![](img/P4_Example_Fluidbed.png)
*Figure 1.1. Particle-Analytics toolbox in use - Post-processing on a fluidized bed. a) Particles visualization.
b) Spatial averaged density. c) Spatial and temporal averaged density over 20 sec.*


The Particle-Analytics Toolbox is implemented within GiD, which is a pre and post-processor software package for numerical simulations.
Detailed manuals for GiD are located at [http://www.gidhome.com/support/manuals](http://www.gidhome.com/support/manuals) while
some tutorials are available at [http://www.gidhome.com/support/tutorials](http://www.gidhome.com/support/tutorials).
GiD is available on a selection of computers but a trial version of the software can be downloaded and used for a three month period on any computer.

