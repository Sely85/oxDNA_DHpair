oxDNA_DHpair
============

Welcome to the oxDNA_DHpair code!  

This code will compute the oxDNA2[1] Debye Huckel interaction for a
specific pair (id1 & id2) in a dump file (generated by LAMMPS[2]).

To determine this electrostatic energy, temperature (in oxDNA units,
0.1 = 300K), salt concentration (mole per liter) and effective charge
(elementary charges) should be written.  If the effective charge is
not chosen, it will be assumed to be qeff = 0.815, as described in
oxDNA2 model.
 
[1] https://dna.physics.ox.ac.uk
[2] https://lammps.sandia.gov


BUILD (Linux)
-------------
g++ -lm -g oxDNA_DH_pair.cpp -o oxDNA_DHpair


USAGE
-----
./oxDNA_DHpair <oxDNAdump> <id1> <id2> <temp> <rhos> <qeff>


EXAMPLE 
------- 
As an example, a file called "2C.dump" has been attached. It containes
only two bases (cytosine) at increasing distances. To compute the
Debye-Huckel energy between those two beads, the following comand
should be used:

./oxDNA_DHpair 2C.dump 1 2 0.098 0.1 

This will compute the Debye Huckel energy between beads with ids 1 and
2, at a temperature of 0.098 and a concentration 0.1M. Since the
effective charge is not written, a value of 0.815 will be used.  The
output is written in a file called "DHenergy.txt", in which the first
column represents the timestep, the second one the distance between
the backbone site of the beads, and the third one will be energy
value.
