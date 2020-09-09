# MATLAB_Examples
Example scripts in MATLAB


Two_Cell_Integrator.m
Two_Cell_Equations.m
Two_Cell_Parameters.m 

You run the integrator and it calls the equations and the parameter files. The integrator page has an ODE solver (ordinary differential equation solver). The non-linear equations are the change in voltage over time for two neurons. We can solve for the end-state of the system over a long time with an ODE solver, or using the Euler method of integration. We are looking for whether the end-state is spiking (action potentials), bursting (trains of action potentials), or silent for each neuron. We are also looking for phase relationships between bursting neurons.

This is a mini intro to Hodgkin-Huxley type neural models

By the definition of capacitance C=q/V, where C is capacitance, q is the
charge and V is voltage (rearrange to get q=C*V)
Then, current, I(t) = C*dV/dt
in our system, we assume the capacitance of the cell membrane to be 1
Thus, I(t)=dV/dt
 
Then, using Kirchoff's Law (the total current is the sum of all currents)
Itot=I1+I2+I3+I4
Our final equation:
dV/dt= I1+I2+I3+I4
 
Imagine we have two cells, and in each of them there are three currents
One for calcium, one for potassium, and one for sodium
What this means is that the cell has 3 types of channels, and each of
these channel types lets one type of molecule through it
So, lets say there is a cell with a bunch of closed sodium channels
these sodium channels then open and let sodium into the
cell, depolarizing it. Here, the value of the sodium current is
increasing from 0 to some value for some amount of time
We also have leak current, which is an ohmic current. 
Gennady Cymbalyuk and his collaborators discovered the importance of
including leak current in Hodgkin-Huxley-type models to accurately
describe cellular behavior
 
 
 
IN THE INTEGRATOR PAGE
The integration script calls the parameter values from the parameter page 
and the equations on the equation page 
You will find the initial conditions for our 14 variables
these won't impact the end-state of the system, unless it is chaotic
But, you don't want to make all of your initial conditions the same
value, or all 0, because the system might get stuck in an 
equilibrated state and might not do anything, or not for a long time
You will find a description of time- for how long
you want to run the script. I have it set to 1000 and this takes 
a minute or two to run and it produces a plot of 
the membrane potentials of cells 1 and 2.
 
 
IN THE EQUATIONS PAGE
The equation page is made into a function - see top of equations page
There is a list of our 14 variables at the top
the equations at the bottom use these variables
 
 
IN THE PARAMETERS PAGE
parameters are constant, while variables change in time
here we have a set of parameters, that describe our cell currents
the cells are identical so one set is sufficient
otherwise, you would have to give them subscripts like 1 for cell 1 
and 2 for cell 2 (eg gCaL1=5. gCaL2=1.)
 
parameters starting with a g are the maximal conductances of some current
gCaL is the maximal conductance of the calcium current
we say maximal conductance because the process of channels
opening is not instantaneous, so the current value increases from 0
to the maximal value... by multiplication by a boltzmann-type function
this method is commonly used in neuro models. 
look up Boltzmann function and imagine why multiplying some parameters value
by this function, that increases from 0 to 1 would correspond to increase
from 0 to a maximal conductance value when all channels are open
(see Boltzmann function on Equations Page)
minf functions are activation of current and hinf are inactivation of
current so minf looks like an S-curve going from zero to one and hinf
looks like an S-curve going from one to zero
 
When these currents have a non-zero value their multiplication by (V-E)
has a non-zerovalue. V is the voltage and E is the reversal potential.
This means that now the voltage tends towards the reversal potential
value
 
parameters starting with an E are the reversal potentials for some current
look up reversal potential on wikipedia 
(there is a section on mathematical models)
 
parameters starting with gSyn are the maximal conductances of synapses
when a cell talks to an other cell it is modeled like an increase in
current from 0 to some maximal value, just like in channels opening.
