.. _appendix:

==========
Appendix C
==========

In this appendix, contents of the files dumped by STATE are described

ENERGIES
--------

- 1st column: ``MDSTP``: MD step
- 2nd column: ``ITER_SCF``: # of electronic SCF cycle in MDSTP step
- 3rd column: ``TEMPP``: Ionic temperature in Kelvin
- 4th column: ``ETOTAL``: Total energy in Hartree
- 5th column: ``ECONS``: Conservation energy (EKINP+ETOTAL+ENOSP) in Hartree
- 6th column: ``DISA``: Mean square displacement of ions

When restarted, new data are appended following the line::

   <<<<<<  NEW DATA  >>>>>>


TRAJECTORY
----------
- 1st column    : ``MDSTP``: MD step
- 2nd-4th column: ``CPS(I,1:3)``: Atomic positions of I-th ion in the Cartesian coordinate (in Bohr radius)
- 5th-7th column: ``CPD(I,1:3)``: Velocity of I-th ion in the Cartesian coordinate (in Bohr atomic unit)

When restarted, new data are appended following the line::

   <<<<<<  NEW DATA  >>>>>>

