.. _utility:

========
Utility
========

.. warning::
        This page is under construction

There are several utility programs for pre- and post-processing for the STATE code, which are located in the ``utility`` directory.

chkinpf
-------
This program performs the minimum test of the input file.
``chkinpf`` also generates a VESTA or XSF file to check the input geometry.

Usage::

  $ chkinpf [input_file]

Type::

  $ chkinpf -h

for other options.

geom2nfinp
----------
This program generates an XYZ/XSF file or STATE input file from the ``GEOMETRY`` file.

Usage::

	$ geom2nfinp -i [STATE input] -o [output file] -g [GEOMETRY file] [-xyz|-xsf] [-h]

The "output file" is the XYZ/XSF or STATE new input file.

Type::

	$ geom2nfinp -h

for help.

state2ev.sh
-----------
This program extract energy and total energy from the STATE output file.

Usage::

	$ state2ev.sh [STATE output1] [STATE output2] ... [STATE outputN]

eosfit
------
This program fits the total energy as a function of volume to the Murnaghan equation of states.

Usage::

	$ eosfit [E-V data]

where [E-V data] should contain volume (Bohr^3, 1st column) and total energy (Hartree, 2nd column).
Estimated total energy, volume, bulk modulus at the equilibrium are printed to ``eosfit.param``.

energy2band
-----------
This program convert the ``energy.data`` file generated in the band structure calculation.
Numbers of bands and k-points, and the energy zero should be specified.

Usage::

	$ energy2band

state2pdos.pl
-------------
This script extracts density of states projected onto atomic orbitals (AOLDOS) from the STATE output.

Usage::

	$ state2pdos.pl [STATE output]

.. note::
        In the spin-polarized case ``NSPIN=2``, spin-up and spin-down PDOSs are printed in the output. Use ``wc`` to count the line number and ``split`` to divide the data.

chg2xsf
-------
This program converts ``nfchgt_r.data``, charge density data in the native STATE format, into the XSF format. This can be used to visualize the LDOS data for the STM simulation.

state2chgpro.sh
---------------
This script extract the planar averages of charge density, local (hartree + XC) potential, and hartree potential from the STATE output.

Usage::

	$ state2chgpro.sh [STATE output]

gif
---
This program reads the calculated forces, constructs the dynamical matrix, and compute the vibrational frequencies. Eigen modes are also printed.

Usage::

	$ gif -f nffroce.data

For other options, type::

	$ gif -h
