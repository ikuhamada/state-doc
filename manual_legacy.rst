.. _Legacy_manual:

:orphan:

=================================
Manual for the legacy STATE input 
=================================

.. warning::
	This page is under construction

Aside from the free format, the current STATE code can also read the legacy fixed input format.
Here is an example of a CO molecule in a small box with the Gamma-point sampling::

  0  0  0  0  0  0                      : dummy line (6 integers)
  5.50 20.00  2  2  2                   : GMAX, GMAXP, NTYP, NATM, NATM2
  1  0                                  : NUM_SPACE_GROUP TYPE
  6.00  4.00  4.00  90.00  90.00  90.00 : A, B, C, ALPHA, BETA, GAMMA
  1  1  1  1  1  1                      : KNX, KNY, KNZ, K-POINT SHIFT
  1  0                                  : NCORD, NINV
  0.0000  0.0000  0.0000  1  1  1       : CPS, IWEI, IMDTYP, ITYP
  2.2000  0.0000  0.0000  1  1  2       : CPS, IWEI, IMDTYP, ITYP
  6  0.1500  51577.50 3 1 0.d0          : IATOMN, ALFA, AMION, ILOC, IVAN, ZETA1
  8  0.1500  51577.50 3 1 0.d0          : IATOMN, ALFA, AMION, ILOC, IVAN, ZETA1
  0  0  0  0  0                         : ICOND, INIPOS, INIVEL, ININOSE, INIACC
  0  1                                  : IPRE, IPRI
  200  200   0    57200.00  0           : NMD1, NMD2, ITER_LAST, CPUMAX, IFSTOP
  3   1                                 : WAY_MIX, MIX_WHAT
  0    8  0.8                           : STARTING_MIXING, KMXMIX, MIX_ALPHA
  0.60  0.50  0.60  0.70  1.00          : DTIM1, DTIM2, DTIM3, DTIM4, DTIM_LAST
  30.00    2     1  0.10D-08 1.d-06     : DTIO, IMDALG, IEXPL, EDELTA
   0.0010  0.10D+02    0                : WIDTH, FORCCR, ISTRESS
 ggapbe          1                      : XCTYPE, NSPIN
   1.00                                 : DESTM
 102                                    : NBZTYP
    0   0   0                           : NKX,  NKY,  NKZ  (dummy)
    0   0   0                           : NKX2, NKY2, NKZ2 (dummy)
    8                                   : NEG (# of bands)
        1                               : NEXTST (1: G-space, 0: R-space)
        0                               : 0; random numbers, 1; matrix diagon
        2                               : IMSD (2: Davidson, 1: RMM)
        0                               : EVAL_EKO_DIFF
        0                               : NPDOSAO
        0    0.0                        : SM_dopping

In the following, each line/block is described one by one.

Dummy line
""""""""""
::

  0  0  0  0  0  0                      : dummy line (6 integers)

For historical reason this line remains and needs to be given in the input file.
Note that this line is used by a utility program "repeat.f."

Cuotff energies, number of atomic species, number of atoms
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
::

  5.50 20.00  2  2  2                   : GMAX, GMAXP, NTYP, NATM, NATM2

- ``GMAX``: Maximum wave number corresponding to the kinetic energy cutoff (in Rydberg) for the wave functions. :math:`E_{\rm{cut}}^{\rm{wf}} = {\rm{GMAX}}^2`
- ``GMAXP``: Maximum wave number corresponding to the kinetic energy cutoff (in Rydberg) for the augmenation charge. :math:`E_{\rm{cut}}^{\rm{dens}} = {\rm{GMAXP}}^2`
- ``NTYP``: Number of atomic species.
- ``NATM``: Number of inequivalent atoms by the inversion symmetry in the unit cell.
- ``NATM2``: Number of total atoms in the unit cell.

In the current version, inversion symmetry is not taken into account and thus always NATM should equal to NATM2.

Symmetry and bravis lattice type
""""""""""""""""""""""""""""""""
::

  1  0                                  : NUM_SPACE_GROUP, TYPE

- ``NUM_SPACE_GROUP``: space group number

- ``TYPE``: Bravis lattice type

==== ===============
TYPE Bravis lattice
==== ===============
0    simple
1    body-centered
2    face-centered
3    a-face-centered
4    b-face-centered
5    c-face-centered
6    rhombohedral
==== ===============

Lattice vectors
"""""""""""""""
::

  6.00  4.00  4.00  90.00  90.00  90.00 : A, B, C, ALPHA, BETA, GAMMA

- ``A``, ``B``, ``C``: length of the first, second, and third lattice vectors.
- ``ALPHA``, ``BETA``, ``GAMMA``: Angles between second and third, third and first, and first and second lattice vectors.

Alternatively, one can define the lattice vectors by using the keyword "Cartesian" followed by the lattice vectors in the Cartesian coordinate as::

 Cartesian
  6.00  0.00  0.00
  0.00  4.00  0.00
  0.00  0.00  4.00

K-point mesh
""""""""""""
::

  1  1  1  1  1  1                      : KNX, KNY, KNZ, K_POINT SHIFT

First 3 integers are used to define the k-point mesh.
Remaining 3 integers are used to define the k-point shift [1 for nonshifted grid and 2 for shifted grid (Monkhorst-Pack grid)].

.. note::
	For the hexagonal systems, it is recommended to use nonshifted k-point grid to avoid the symmetry breaking.

Unit of the atomic coordinate, inversion symmetry
"""""""""""""""""""""""""""""""""""""""""""""""""
::

  1  0                                  : NCORD, NINV

- ``NCORD``

= =========================================================================
1 Cartesian coordinate (in Bohr radius)
0 reduced coordinate (coordinate in the unit of primitive lattice vectors)
2 coordinate in the unit of conventional lattice vectors
= =========================================================================

- NINV

= =====================
0 no inversion symmetry
1 inversion symmetry
= =====================

_note::
``NINV=0`` is not maintained in the current version of STATE, but the number of atoms can be almost halved when ``NINV=1`` is activated, if it is implemented.

Atomic positions and types
""""""""""""""""""""""""""
::

  0.0000  0.0000  0.0000  1  1  1       : CPS, IWEI, IMDTYP, ITYP
  2.2000  0.0000  0.0000  1  1  2       : CPS, IWEI, IMDTYP, ITYP

- 1-3 columns: ``CPS`` (``POS``) Atomic coordinates.
- 4th column: ``IWEI`` Number of equivalent atoms by the inversion symmetry (OBSOLETE)
- 5th colum: ``IMDTYP`` Set 1 when the atom is allowed to move, otherwise set 0.
- 6th column: ``ITYP`` Atomic type

(Pseudo) atoms
""""""""""""""
::

  6  0.1500  51577.50 3 1 0.d0          : IATOMN, ALFA, AMION, ILOC, IVAN, ZETA1
  8  0.1500  51577.50 3 1 0.d0          : IATOMN, ALFA, AMION, ILOC, IVAN, ZETA1

- 1st column: ``IATOMN`` Atomic number
- 2nd column: ALFA Initial charge (dummy)
- 3rd column: ``AMION`` Atomic mass in a.m.u.
- 4th column: ILOC Angular momentum for the local potential (l_loc +1) (dummy)
- 5th column: IVAN Integer to specify if ultrasoft pseudopotential is used (1) or not (0) (dummy)
- 6th column: ``ZETA1`` Initial magnetization

Restart options for the wave functions
""""""""""""""""""""""""""""""""""""""
::

  0  0  0  0  0                         : ICOND, INIPOS, INIVEL, ININOSE, INIACC

- ``ICOND``: Restart option for the wave functions and option for the electronic structure analysis

=== ===========================================================================================================================
0   Initialize the wave function. This is used to start an SCF calculation from scratch.
1   Restart SCF by using the existing wave function and charge density (potential). zaj.data and potential.data are necessary.
2   Fixed charge calculation. Wave functions are calculated from scractch. potentil.data is necessary.
3   Restart the fixed charge calculation.
4   Fixed charge calculation (same as ``ICOND=2``).
9   Print the total charge density in real space.
11  Print the soft part of the charge density in real space.
10  Simple STM simulation.
12  DOS calculation.
14  Partial density of states (PDOS) calculation.
24  K-point resolved partial density of states (PDOS) calculation.
15  Print the wave functions in real space.
115 Print the wave functions in real space. Used for the band structure calculation (``ICOND=22``)
17  Crystal orbital overlap population (COOP) analysis 
117 K-point resolved crystal orbital overlap population (COOP) analysis
22  Band structure calculation.
23  Restart the band structure calculation.
33  Atomic layer resolved density of states (ALDOS) calculation.
133 Old ALDOS
40  Generate wave functions and potential.data for GWST (version 5.3.8b)
41  Generate wave functions along the high symmetry points and potentials for GWST (version 5.3.8b)
=== ===========================================================================================================================

- ``INIPOS``: Restart options for the atomic positions

= =========================================================================================
0 Read the atomic positions from the input file.
1 Restart by reading the atomic positions from "restart.data."
2 Restart by reading the atomic positions from "GEOMETRY" (restart.data is also required).
= =========================================================================================

- ``INIVEL``: Restart options for the atomic positions

= =========================================================================================
0 Initialize the velocity
1 Restart by reading the velocities from "restart.data."
2 Restart by reading the velocities from "GEOMETRY" (restart.data is also required).
= =========================================================================================

- ``ININOS``: Restart options for the Nose thermostat

= =========================================================================================
0 Initialize the thermostat
1 Restart the thermostat
= =========================================================================================

- ``INIACC``: Restart options for the accumulator

= =========================================================================================
0 Initialize the accumulator
1 Restart the accumulator
= =========================================================================================

- Examples of restart


Restart only SCF (geometry from input) ::

  1  0  0  0  0                         : ICOND,INIPOS,INIVEL,ININOS, INIACC

Restart the structural optimization ::

  1  1  0  0  0                         : ICOND,INIPOS,INIVEL,ININOS, INIACC

Restart the structural optimization by referring the GEOMETRY file ::

  1  2 0  0  0                         : ICOND,INIPOS,INIVEL,ININOS, INIACC

Restart the structural optimization, but refresh the wave functions ::

  0  1  0  0  0                         : ICOND,INIPOS,INIVEL,ININOS, INIACC

Restart the molcular dynamics ::

  1  1  1  0  0                         : ICOND,INIPOS,INIVEL,ININOS, INIACC

or ::

  1  1  1  1  1                         : ICOND,INIPOS,INIVEL,ININOS, INIACC

Stress, print level
"""""""""""""""""""
::

  0  1                                  : IPRE, IPRI

- ``IPRE``: 1 for the stress calculation (not implemented)
- ``IPRI``: verbosity of the output. Use IPRI>1 for debugging.

Numbef of SCF, structural optimization/MD, CPU time
"""""""""""""""""""""""""""""""""""""""""""""""""""
::

  200  200   0    57200.00  0           : NMD1, NMD2, ITER_LAST, CPUMAX, IFSTOP

- ``NMD1``: Maximum number of SCF steps.
- ``NMD2``: Maximum number of molecular dynamics step. NMD2+1 is the actural number of steps.
- ITER_LAST
- ``CPUMAX``: Maximu CPU time in second.
- IFSTOP

Mixing scheme, object to be mixed
"""""""""""""""""""""""""""""""""
::

  3   1                                 : WAY_MIX, MIX_WHAT

- ``WAY_MIX``

= ==============
1 simple mixing
2 Broyden
3 Broyden2
4 DFP
5 Pulay
6 Blugel
= ==============
 
- ``MIX_WHAT``

= ==============
1 charge density
2 potential 
= ==============

Mixing parameter
""""""""""""""""
::

  0    8  0.8                           : STARTING_MIXING, KMXMIX, MIX_ALPHA

- STARTING_MIXING: dummy
- ``KBXMIX``: number of previous charges/potentials to be used in the mixing.
- ``MIX_ALPHA``: mixing parameter.

Mixing parameters for RMM-DIIS
""""""""""""""""""""""""""""""
::

  0.60  0.50  0.60  0.70  1.00          : DTIM1, DTIM2, DTIM3, DTIM4, DTIM_LAST 

- DTIM: Mixing parameter for RMM-DIIS. Only ``DTIM2`` is used.
- DTIM_LAST: Dummy.

Time step, MD algorithm, convergence threshold
""""""""""""""""""""""""""""""""""""""""""""""
::

  30.00    2     1  0.10D-08 1.d-06     : DTIO,IMDALG,IEXPL,EDELTA

- ``DTIO``: Molecular dynamics time step in the atomic unit (1 a.u.=0.024188 fs, 41.3428 a.u.=1 fs)
- ``IMDALG``: Molecular dynamics algorithm.

== ===================================================
 1 Newtonian dynamics
 2 Quenched molecular dynamics
 3 Vibrational mode analysis¡(nfvibrate.data required)
 4 GDIIS
 5 TS search by GDIIS
 6 Nudged elastic band method
 7 Climbing image NEB method
 0 Newtonian dynamics
-1 Finite temperature Newtonian dynamics¡
-2 Langevin MD
== ===================================================

- IEXPL: dummy
- ``EDELTA``: Threshold (total energy per atom) for the electronic system. Use 1.d-9 - 1.d-11.

Smearing, force threshold, stress
"""""""""""""""""""""""""""""""""
::

   0.0010  0.10D+02    0                : WIDTH, FORCCR, ISTRESS

- ``WIDTH``: Smearing width. Use negative value (>-10.0) for the Hermite-Gaussian smearing. Use a value < -10.0 for the tetrahedron method.
- ``FORCCR``: Force threshold for the structural optimization.
- ISTRESS: 1 for stress calculation (not yet implemented)

Exchange correlation and spin
"""""""""""""""""""""""""""""
::

 ggapbe          1                      : XCTYPE, NSPIN

- ``XCTYPE``

=========== ===================================
ggapbe      Perdew, Burke, Ernzerhof GGA (1996)
ggapw91     Perdew-Wang GGA (1991)
ldapw91     Perdew-Wang L(S)DA (1991)
rpbe        revised PBE of Hammer et al.
revPBE      revised PBE of Zhang and Yang
wc          Wu-Cohen GGA
vdW-DF1     vdW-DF of Dion et al's
vdW-DF2     vdW-DF of Lee et al's
optB88-vdW  vdW-DF of Klimes et al's
optB86b-vdW vdW-DF of Klimes et al's
rev-vdW-DF2 vdW-DF of Hamada's
=========== ===================================

- ``NSPIN``

= ========================
1 spin unpolarized system
2 spin polarzed system
= ========================

STM
"""
::

   1.00                                 : DESTM

- ``DESTM``: STM bias in volt.

Type of sampling of G-vectors for the tetrahedron method
""""""""""""""""""""""""""""""""""""""""""""""""""""""""
::

 102                                    : NBZTYP

- ``NBZTYP``: specify how to sampel G vectors in the tetrahedron method. NBZTYP=101 is recommended

Dummy lines
"""""""""""
::

    0   0   0                           : NKX,  NKY,  NKZ  (dummy)
    0   0   0                           : NKX2, NKY2, NKZ2 (dummy)

Number of bands
"""""""""""""""
::

    8                                   : NEG (# of bands)

- ``NEG``: The number of bands considered in the calculation. Always use number of bands, which is slightly larger than the half of the number of valence electrons.

nonlocal pseudopotential scheme
"""""""""""""""""""""""""""""""
::

        1                               : NEXTST (1: G-space, 0: R-space)

- ``NEXTST``

= =====================================================
0 R-space (Do not use when the Davidson scheme is usd)
1 G-space
= =====================================================

Dummy line
""""""""""
::

        0                               : 0; random numbers, 1; matrix diagon

Diagonalization method
""""""""""""""""""""""
::

        2                               : IMSD (2: Davidson, 1: RMM)

- ``IMSD``

= ========
1 RMM-DIIS
2 Davidson
= ========

.. note::
	For a large scale calculation, RMM-DIIS and real space projection is recommended (NEXTST=0 & IMSD=1). In such a case, prepare the wave functions with the Davidson scheme (NEXTST=1 & IMSD=2) and restart with RMM-DIIS.

Evaluate the eigenvalue difference
"""""""""""""""""""""""""""""""""""
::

        0                               : EVAL_EKO_DIFF: .0 = no ,1 = yes

- ``EVAL_EKO_DIFF``: Evaluate the eigenvalue difference from the previous step (1 to activate this). Unused currently.

PDOS option
"""""""""""
::

        0                                                   : NPDOSAO

When ``NPDOSAO>0``, the PDOS calculation is performed. NPDOSAO indicates the number of atomic orbitals onto which DOSs are calculated. See below.

Empirical parameters for the f electrons (dummy)
""""""""""""""""""""""""""""""""""""""""""""""""
::

        0    0.0      

