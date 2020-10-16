.. _Manual:

======
Manual
======

Complete list of STATE input variables. Atomic unit is used unless otherwise specified.

Click :any:`here <Legacy_manual>` for the legacy input manual. 

WF_OPT
	Type: character

	Default: DAV

	Description:

	Wave function optimization method.

	* DAV: Davidson

	* RMM: RMM-DIIS


NLPROJ
	Type: character

	Default: RECIP

	Description:

	Method for the nonlocal pseudopotentials.

	* RECIP | G-SPACE: reciprocal space projection

	* REAL | R-SPACE: real space projection 


GEO_OPT
	Type: character

	Default: QMD

	Description:

	Geometry optimization method.

	* QMD: Quenched molecular dynamics (aka quick-min)

	* GDIIS: generalized DIIS method

	* FIRE: Fast Inertial Relaxation Engine

	* NEB: Nudged elastic band method to find saddle points and minimum energy paths

	* CINEB: Climbing-image NEB method


ION_DYN
	Type: character

	Default: none

	Description:

	Molecular dynamics method.

	* FTMD: Finite temperature molecular dynamics

	* ZTMD: Newtonian dynamics at 0 K

	* LANGEVIN: Langevin molecular dynamics


RESTART
	Type: character

	Default: none

	Description:

	Use this keyword to restart the calculation.

	* None: wave funcitons, geometry, and velocity are read from the restart file

	* WF: wave function is read from the restart file

	* POS: geometry is read from the restart file

	* VEL: velocity is read from the restart file

	* NOS: Nose thermostat is read from the restart file

        * RESTART_FILE: geometry and velocities are read from the restart file ("restart.data"). Wave function are calculated from scratch if not specified.

        * GEOMETRY_FILE: geometry and velocities are read from the GEOMETRY file. Wave function are calculated from scratch if not specified.


VIBRATION
	Type: character

	Default: none

	Description:

	Use this keyword to perform the vibrational mode analysis.
	A file 'nfvibrate.data' is required to specify the atomic displacements.


PRINT_RHO
	Type: character

	Default: none

	Description:

	Use this keyword to print the charge density in real space


DOS
	Type: character

	Default: none

	Description:

	Use this keyword to print the total density of states


PDOS | AOLDOS
	Type: character

	Default: none

	Description:

	Use this keyword to print the density of states projected onto the atomic orbital. The &PDOS...&END block should be added.


ALDOS
	Type: character

	Default: none

	Description:

	Use this keyword to performe the atomic layer resolved density of states analysis.


COOP
	Type: character

	Default: none

	Description:

	Use this keyword to generate data for the COOP analysis


BAND
	Type: character

	Default: none

	Description:

	Use this keyword to perform the band structure analysis


STM_SIMPLE
	Type: character

	Default: none

	Description:

	Use this keyword to perform a simple STM simulation based on the Tersoff-Hamann theory.


STM
	Type: character

	Default: none

	Description:

	Use this keyword to perform a precise STM simulation based on the Tersoff-Hamann theory. Need to add the &STM...&END block.


TASK
	Type: character

	Default: none

	Description:

	This keyworkd is used to specify the task, but the keyword ``TASK`` can be omitted as above.
	Available options are as follows:

	* SCF | WF_OPT : SCF calculation

	* NSCF : Non-SCF calculation

	* BAND : Band structure calculation

	* OPT | GEO_OPT : Structural optimization

	* MD | FTMD : Finite temperature molecular dynamics

	* ZTMD : Zero temperature molecular dynamics

	* NEB : Nudged elastic band calculation

	* CINBE : Climbing-image nudged elastic band calculation

	* VIB : Vibrational mode analysis

	* PRTRHO : Print the charge density in real space

	* DOS : Print the total density of states

	* PDOS : Print the density of states projected onto atomic orbital (AOLDOS)

	* PRTWFC : Print wave function(s) in real space

	* PRTWFC_BAND : Print wave function(s) in real space

	* COOP : Crystal orbital overlap population analysis (post-processing required)

	* ALDOS : Atomic layer resolved local density of states calculation

	* STM: Scanning tunneling microscopy (STM) simulation based on the Tersoff-Hamann theory

	* STM_SIMPLE: Simplified STM simulation based on the Tersoff-Hamann theory


GMAX
	Type: real

	Default: none

	Description:

	Wave vector cutoff for the wave functions in the atomic unit.
	GMAX**2 corresponds to the cutoff energy in Rydberg.

GMAXP
	Type: real

	Default: none

	Description:

	Wave vector cutoff for the (augmentation) charge in the atomic unit.
	GMAXP**2 corresponds to the cutoff energy in Rydberg.

NTYP
	Type: integer
	
	Default: none
	
	Description:

	Number of atomic species

NATM
	Type: integer

	Default: none

	Description:

	Number of atoms in the system.
	
BRAVIS_TYPE | TYPE
	Type: integer

	Default: 0

	Description:

	Type of Bravis lattice.

	* 0: SImple lattice

	* 1: Body-centered cubic

	* 2: Face-centered cubic

	* 3: A-centered lattice

	* 4: B-centered lattice

	* 5: C-centered lattice

	* 6: Rhombohedral lattice

BRAVIS_LATTICE
	Type: character

	Default: Simple

	Description:

	Type of Bravis lattice.	

	* SIMPLE: Simple lattice

	* BCC: Body-centered cubic

	* FCC: Face-centered cubic

	* A_CENTER: A-centered lattice

	* B_CENTER: B-centered lattice

	* C_CENTER: C-centered lattice

	* RHOMBO | TRIG: Rhombohedral lattice

NSPG
	Type: integer

	Default: 1

	Description:

	Space group number.

CELL
	Type: real array

	Default: 0.0 0.0 0.0 0.0 0.0 0.0

	Description:

	Lengths of first, second, and third vectors (A, B, and C), and angles (in degree) between, second and third, third and first, and first and second vectors (ALPHA, BEGA, GAMMA).
        These parameters define the basic lattice vectors of the conventional unit cell.
        In this way, the first lattice vector :math:`a_1` is along the x-axis, the second lattice vector :math:`a_2` is in the xy plane, and the third vector :math:`a_3` is determined depending on the angle with :math:`a_1` and :math:`a_2`.

KPOINT_MESH
	Type: integer array

	Default: 1 1 1 

	Description:

	K-point mesh along the first, second, and third reciprocal lattice vectors.

KPOINT_SHIFT
	Type: character array

	Default: F F F

	Description:

	Shift for the k-points in the direction of the first, second, and third reciprocal lattice vectors.

	* F/OFF: non-shifted

	* T/ON: shifted

KPOINT_SHIFT_OLD
	Type: integer array

	Default: 1 1 1

	Description:

	Shift for the k-points in the direction of the first, second, and third reciprocal lattice vectors. K-point shifts according to the legacy input (M1, M2, and M3).

	* 1: non-shifted

	* 2: shifted


KPOINTS
	Type: integer array
	
	Default: 1 1 1 1 1 1

	Description:

	Combined keyword for k-point mesh and shift.

COORD
	Type: character

	Default: CARTESIAN

	Description:

	Unit/format of atomic coordinates in the &ATOMIC_COORDINATES...&END block.

	* CRYSTAL: crystal (reduced) coordinate

	* CARTESIAN: cartesian coordinate

	* CONVENTIONAL: crystal (reduced) coordinate of the conventional unit cell

	* XYZ: atomic coordinates are given in the XMOL xyz format (Angstrom, NOT Bohr)

NCORD
	Type: integer

	Default: 1

	Description:

	Unit of atomic coordinates.

	* 0: crystal coordinate

	* 1: cartesian coordinate

	* 2: crystal coordinate (conventional unit cell)

NINV
	Type: integer
	
	Default: 0

	Description:

	Keyword to specify the inversion symmetry.

	* 1: with inversion symmetry

	* 0: no inversion symmetry

ICOND
	Type: integer

	Default: 0

	Description:

	Integer to define the calculation.

	* 0: Calculation of the wave functions from scratch

	* 1: Restart with the last wave functions

	* 2: Fixed charge calculation with the wave functions from scratch

	* 3: Fixed charge calculation with the last wave functions

	* 9: Generation of the charge density in real space

	* 10: Simple STM simulation based on the Tersoff-Hamann theory

	* 11: Generation of the soft-part of the charge density in real space

	* 12: Density of states calculation

	* 14: Partial density of states calculation

	* 15: Generation of the wave function in real space
	
	* 17: Crystal orbital overlap population analysis

	* 21: STM simulation based on the Tersoff-Hamann theory

	* 33: Atomic layer resolved density of states calculation

INIPOS
	Type: integer

	Default: 0

	Description:
	
	Restart option for the atomic positions

	* 0: From input
	
	* 1: From restart.data
	
	* 2: From GEOMETRY

INIVEL
	Type: integer

	Default: 0

	Description:
	
	Restart option for the velocities

	* 0: From input
	
	* 1: From restart.data
	
	* 2: From GEOMETRY

ININOS
	Type: integer

	Default: 0

	Description:
	
	Restart option for the Nose thermostat

	* 0: From input
	
	* 1: From restart.data
	
INIACC
	Type: integer

	Default: 0

	Description:
	
	Restart option for the accumulator

	* 0: From input
	
	* 1: From restart.data

NSCF
	Type: integer
	
	Default: none

	Description: 

	Number of SCF steps.

NSTEP
	Type: integer
	
	Default: none

	Description:

	Number of ionic steps.

CPUMAX
	Type: real
	
	Default: none

	Description:

	Max. CPU time in second.

WAY_MIX
	Type: integer

	Default: none

	Description:

	Integer to specify the mixing method.

	* 1: simple

	* 2: Broyden1

	* 3: Broyden2

	* 4: DFP

	* 5: Pulay

	* 6: Blugel

MIX_WHAT
	Type: integer

	Default: 1

	Description:

	Integer to specify the object to be mixed.

	* 1: Charge density

	* 2: Potential

MIX
	Type: character

	Default: BLUGEL

	Description:

	Mixing scheme.

	* SIMPLE: simple mixing

	* BROYDEN: Broyden mixing

	* BROYDEN2: Broyden2 mixing

	* PULAY: Pulay mixing

	* BLUGEL: Bluegel-Ishida mixing scheme 

MIXOBJ
	Type: character

	Default: CHARGE

	Description:

	Mixing object.

	* CHARGE: charge density

	* POTENTIAL: potential


KBXMIX
	TYpe: integer

	Default: none

	Description:

	Number of charges/potentials to be stored for the mixing.


MIX_ALPHA
	Type: real

	Default: 0.7

	Description:
	
	Mixing parameter.


LABMDA_RMM
	Type: real

	Default: 0.3

	Description:
	
	Mixing parameter for the RMM-DIIS scheme.


WIDTH
	Type: real
	
	Default: -0.001

	Description:

	Smearing width. The 1st-order Hermite-Gaussiang smearing is used when the negative value is used (if < -10.0, tetrahedron method is used)
	When the variable ``SMEARING`` is set, positive ``WIDTH`` can be used. 


EDELTA
	Type: real

	Default: 1.e-9

	Descritoin:

	Convergence threshold for the total energy.


NBZTYP
	Type: integer
	
	Default: 101

	Description:
	
	Integeger to specfy which tetrahedron method is used.

	* 100: tetrahedron method with reduced G vectors

	* 101: linear corrected tetrahedron method with extended G vectors 

	* 102: linear corrected tetrahedron method with reduced G vectors


BZINT
	Type: character

	Default: none

	Description:

	Brillouin zone integration scheme.

	* TETRA: Linear tetrahedron method

	* TETRA_RED: Linear tetrahedron method with reduced G-vectors


SMEARING
	Type: character

	Default: none

	Description:

	Smearing scheme.

	* FD: Fermi-dirac distribution function

	* MP | MP1 | HG1: Methfessel-Paxton Hermite-Gaussian function of the order 1

	* MP2 | HG2: Methfessel-Paxton Hermite-Gaussian function of the order 2

	* GA: Gaussian function

	* MV: Marzari-Vanderbilt cold smearing


NEG
	Type: integer
	
	Default: none

	Description:

	Number of bands considered in the calculation.


IMDALG
	Type: integer
	
	Default: 2

	Description:
	
	Integer to specify the molecular dynamics algorithm.

	* -2: Langevin molecular dynamics simulation

	* -1: Molecular dynamics simulation at finite temperature

	* 1: Newtonian dynamics at zero temperature

	* 2: Geometry optimization by quenched molecular dynamics

	* 3: Vibrational mode analysis in harmonic approximation

	* 4: Geometry optimization by DIIS method

	* 5: Transition state search by GDIIS method

	* 6: Reaction path search by nudged elastic band method

	* 7: Reaction path search by clinmbing image nudged elastic band method


DTIO
	Type: real
	
	Default: 50.0

	Description:

	Time step for the molecular dynamics / geometry optimization.


FORCCR | FMAX
	Type: real
	
	Default: none

	Description:

	Force threshold for the geometry optimization.

ISTRESS
	Type: integer
	
	Default: 0

	Description:

	If ISTRESS is set to 1, the stress tensor is calculated (not yet implemented).

XCTYPE
	Type: character
	
	Default:
	
	ggapbe 

	Description:

	Type of the exchange-correlation functional used.

	* ldapw91 (LDA) Perdew-Wang '92

	* ggapbe (GGA) Perdew-Burke-Ernzerhof '96
	
	* revpbe (GGA) revised PBE of Zhang and Yang

	* rpbe (GGA) revised PBE of Hammer ... Norskov

	* wc (GGA) Wu-Cohen GGA

	* pbesol (GGA) PBEsol of Perdew et al.

	* vdw-df/drsll (vdW-DF) vdW-DF(1) of Dion et al.
	
	* vdw-df2/lmkll (vdW-DF) vdW-DF2 of Lee et al.

	* c09/c09-vdw/drsllc (vdW-DF) vdW-DF-C09 of Cooper

	* c09-vdw2/lmkllc (vdW-DF) vdW-DF2-C09 of Hamada

	* optb88/optb88-vdw/kbm (vdW-DF) optB88-vdW of Klimes

	* optpbe/optpbe-vdw (vdW-DF) optPBE-vdW of Klimes

	* optb86b/optb86b-vdw (vdW-DF) optB86b-vdW of Klimes

	* rev-vdw-df2/lmkllh (vdW-DF) rev-vdW-DF2 of Hamada

	* vdw-df-cx/bh (vdW-DF) Berland and Hyldgaard

NSPIN
	Type: integer
	
	Default: 1

	Description:

	Number of spin component.

	* 1: spin unpolarized case

	* 2: spin polarized case

DESTM
	Type: real

	Default: none
	
	Description: STM bias in Volt

NEXTST
	Type: integer

	Default: 1
	
	Description:

	Integer to specify the method of the nonlocal pseudopotential projection.

	* 1: reciprocal space

	* 2: real space

IMSD
	Type: integer

	Default: 2
	
	Description:

	Integer to specify the method of the electronic minimization.

	* 1: RMM-DIIS

	* 2: Davidson

NPDOSAO
	Type: integer

	Default: 0
	
	Description:

	Number of atoms for which the projected density of states are calculated

TEMP_CONTROL
	Type: integer

	Default: VELSC

	Description:

	This keyword defines the ensemble method for the finite temperature molecular dynaics simulation

	* MICRO: Microcanonical 

	* SA: Simulated annealing

	* VELSC: Simple velocity rescaling

	* MA: Rolling average

	* GT: Gauusian thermostating method

	* NHC: Nose-Hoover chain

	* GGMT: Generalized Gaussian Moment thermostating (GGMT) method

MVELSC
	Type: integer

	Default: 2
	
	Description:

	Integer to define the method of velocity control for the finite temperature molecular dynamics simulation

	* 0: Microcanonical

	* 1: Simulated annealing

	* 2: Simple velocity rescaling

	* 3: Rolling average method

	* 4: Gaussian dynamics

	* 10: Nose-Hoover chain (NHC) method
	
	* 11: Generalized Gaussian Moment thermostating (GGMT) method

TEMPW
	Type: real
	
	Default: 300.0

	Description:

	Target temperature in Kelvin

ANNEAL
	Type: real

	Default:

	Description:

	Annealing factor for the simulated annealing. Square root of ANNEAL is multiplied by ionic velocies at every MD ste.
	
TOLP
	Type: real
	
	Default: 30.0

	Description:

	Tolerance of temperature in Kelvin. This variable is used in the simple velocity rescaling or rolling average method


WNOSEP
	Type: real
	
	Default: 300.0

	Description:

	Characteristic vibrational frequency in wavenumber, which is used to generate the thermostat variables.

NHC
	Type: integer

	Default: none
	
	Description:

	Length of thermostat chain. Up to the order of 2 * NHC Gaussian moments are controlled when GGMT tmethod is used. Suggested value is 4 for NHC and 2 for GGMT.

NOSY
	Type: integer

	Default: none
	
	Description:
	
	The order of Suzuki-Yoshida integrator used to integrate thermostat variables. The averable order is 1, 3, 5, 7, 15, 25, 125, and 625, and suggested value is 15.


NDRT
	Type: integer

	Default: none
	
	Description:
	
	Number of integration cycles for thermostat variables. Usually NDRT=1 is enough for stable integration of thermostat variables.

NROLL
	Type: integer

	Default: none
	
	Description:

	Interval at which the rolling averae is taken. This is used to determine a rescaling factor for velocities in the rolloing average method. Typical value is 10.	

FRICT
	Type: real

	Default: none
	
	Description:
	
	Friction coefficient used to generage random forces for Langevin molecular dynamics

&CELL ... &END
  This block is used to define the unit cell.

  Syntax::

	&CELL
	 [A1(1)] [A1(2)] [A1(3)]
	 [A2(1)] [A2(2)] [A2(3)]
	 [A3(1)] [A3(2)] [A3(3)]
	&END

  * A1(1:3): First lattice vector 

  * A2(1:3): Second lattice vector

  * A3(1:3): Third lattice vector

&ATOMIC_TYPE ... &END
  This block is used to define the atomic types in the legacy STATE format.

  Syntax::

	&ATOMIC_TYPE
	 [ATOMN(1)] [ALFA(1)] [AMION(1)] [ILOC(1)] [IVAN(1)] [ZETA1(1)]
	 [ATOMN(2)] [ALFA(2)] [AMION(2)] [ILOC(2)] [IVAN(2)] [ZETA1(2)]
	 ...
	 [Z(NTYP)] [ALFA(NTYP)] [AMION(NTYP)] [ILOC(NTYP)] [IVAN(NTYP)] [ZETA(NTYP)]
	&END

  ATOMN: Atomic number.

  ALFA: Initial charge (obsolete).

  AMION: Atomic weight in atomic mass unit.

  ILOC: Angular momentum (l_loc + 1) for the local pseudopotential (obsolete)

  IVAN: Specify the type of the pseudopotential. 1 for USPP, otherwise NCPP (obsolete)

  ZETA1: Initial magnetization for each type of element

``&ATOM ... &END`` can be used with the same syntax.


&ATOMIC_SPECIES
  This block is an alternative to the ``&ATOMIC_TYPE`` block, which is used to define the atomic types.
  The syntax is similar to the one in Quantum-ESPRESSO.

  Syntax::

	&ATOMIC_SPECIES
	 ATOMIC_NUMBER(1) ATOMIC_MASS(1) PSEUDOPOTENTIAL_FILE(1) 
	 ATOMIC_NUMBER(2) ATOMIC_MASS(2) PSEUDOPOTENTIAL_FILE(2) 
	 ...
	 ATOMIC_NUMBER(NTYP) ATOMIC_MASS(NTYP) PSEUDOPOTENTIAL_FILE(NTYP) 
	&END

  or::

	&ATOMIC_SPECIES
	 ATOMIC_SYMBOL(1) ATOMIC_MASS(1) PSEUDOPOTENTIAL_FILE(1) 
	 ATOMIC_SYMBOL(2) ATOMIC_MASS(2) PSEUDOPOTENTIAL_FILE(2)
	 ...
	 ATOMIC_SYMBOL(NTYP) ATOMIC_MASS(NTYP) PSEUDOPOTENTIAL_FILE(NTYP) 
	&END


&ATOMIC_COORDINATES ... &END
  This block is used to define the atomic coordinates in the legacy STATE format.

  Syntax::

	&ATOMIC_COORDINATES [CRYSTAL|CRYS|CARTESIAN|CART]
	 CPS(1,1) CPS(1,2) CPS(1,3) IWEI(1) IMDTYP(1) ITYP(1)
	 CPS(2,1) CPS(2,2) CPS(2,3) IWEI(2) IMDTYP(2) ITYP(2)
	 ...
	 CPS(NATM,1) CPS(NATM,2) CPS(NATM,3) IWEI(NATM) IMDTYP(NATM) ITYP(NATM)
	&END
	
	
  CARTESIAN/CART: If set, atomic coordinates are given in the cartesian coordinate

  CRYSTAL/CRYS: If set, atomic coordinates are given in the crystal coordinate

  CPS: Atomic coordinate in the cartesian (NCORD=1 or COORD=CARTESIAN) or in the crystal (NCORD=0 or COORD=CRYSTAL) coordinate

  IWEI: number of equivalent atoms under the inversion symmetry

  IMDTYP:

  * 1: Allow to move the ion

  * 0: Fix the ion

  * -011: Fix the ion in the x-direction

  * -101: Fix the ion in the y-direction

  * -110: Fix the ion in the z-direction

  * -001: Fix the ion in the xy-direction

  * -100: Fix the ion in the yz-direction

  * -010: Fix the ion in the zx-direction

  NOTE It is adviced to use the quenched molecular dynamics for the geometry optimization, when ionic coordinates are constrained.

  It is also possible to define the atomic coordinates in the cartesian coordinate without setting NCOORD or COORD as::

	&ATOMIC_COORDINATES CARTESIAN
	 CPS(1,1) CPS(1,2) CPS(1,3) IWEI(1) IMDTYP(1) ITYP(1)
	 CPS(2,1) CPS(2,2) CPS(2,3) IWEI(2) IMDTYP(2) ITYP(2)
	 ...
	 CPS(NATM,1) CPS(NATM,2) CPS(NATM,3) IWEI(NATM) IMDTYP(NATM) ITYP(NATM)
	&END
	
	
  in the crystal (reduced) coordinate::

	&ATOMIC_COORDINATES CRYSTAL
	 CPS(1,1) CPS(1,2) CPS(1,3) IWEI(1) IMDTYP(1) ITYP(1)
	 CPS(2,1) CPS(2,2) CPS(2,3) IWEI(2) IMDTYP(2) ITYP(2)
	 ...
	 CPS(NATM,1) CPS(NATM,2) CPS(NATM,3) IWEI(NATM) IMDTYP(NATM) ITYP(NATM)
	&END


&INITIAL_ZETA ... &END
  This block is used to define the initial magnetizations. Default values are zero.

  Syntax::

	&INITIAL_ZETA
	 ZETA1(1)
	 ZETA1(2)
	 ...
	 ZETA1(NTYP)
	&END

  ZETA1: Initial magnetization for each type of element


&PDOS ... &END
  This block is used to define the parameters needed to calculated PDOS in the legacy STATE format.

  Syntax::
	
	&PDOS
	 NPDOSAO
	 IPDOST(1) IPDOST(2) ... IPDOST(NPDOSAO)
	 EPDOS(1) EPDOS(2) EPDOS(3) NPDOSE
         RPDOS(1,1) RPDOS(2,1)
         RPDOS(1,2) RPDOS(2,2)
	 ...
	 RPDOS(1,NTYP) RPDOS(2,NTYP)
	&END


  NPDOSAO: Number of atoms for which the projected density of states are calculated

  IPDOST: Index of atom for which the projected density of states are calculated

  EPDOS(1): Minimum energy for the density of states

  EPDOS(2): Maximum energy for the density of states

  EPDOS(3): Smearing width for the Gaussian broadening
  
  NPDOSE: Energy mesh for the density of states calculation.	

  RPDOS(1,I): Cutoff radius for the I-th atomic orbital

  RPDOS(2,I): Smearing width (in real space) for the I-th atomic orbital

  Following synax can also be used::

	&PDOS
	 NPDOSAO [NPDOSAO]
	 IPDOST  [IPDOST(1) IPDOST(2) ... IPDOST(NPDOSAO)]
	 EMIN    [EPDOS(1)]
         EMAX    [EPDOS(2)]
         EWIDTH  [EPDOS(3)]
         NPDOSE  [NPDOSE]
         RCUT    [RPDOS(1,1) RPDOS(1,2) ... RPDOS(1,NTYP)]
         RWIDTH  [RPDOS(2,1) RPDOS(2,2) ... RPDOS(2,NTYP)]
	&END


&DFT+U ... &END
  This block is used to define the parameters needed for the DFT+U calculations.

  Syntax::
	
	&DFT+U
	 NPDOSAO
	 IPDOST(1) UT(1)
	 IPDOST(2) UT(2)
	 ...
	 IPDOST(NPDOSAO) UT(NPDOSAO)
	 EPDOS(1) EPDOS(2) EPDOS(3) NPDOSE
         RPDOS(1,1) RPDOS(2,1)
         RPDOS(1,2) RPDOS(2,2)
	 ...
	 RPDOS(1,NTYP) RPDOS(2,NTYP)
	 LDAU NDMAT
	 U_LDAU J_LDAU
	&END

  NPDOSAO: Number of atoms for which Hubbard correction is applied

  IPDOST: Index of atom for which Hubbard correction is applied

  UT(1:NPDOSAO): Habbard U value

  EPDOS(1): Minimum energy for the density of states

  EPDOS(2): Maximum energy for the density of states

  EPDOS(3): Smearing width for the Gaussian broadening
  
  NPDOSE: Energy mesh for the density of states calculation.	

  LDAU: Dummy integer. Always set to 1

  NDMAT: Number of density matrix to be read from a file

  U_LDAU: Habbard U value

  J_LDAU: Habbard J value

&VDW_CORRECTION ... &END
 This block is used to add the van der Waals correction of Grimme's DFT-D2.
 C6 parameters are hard coded in VanDerWaals.f90.

  Syntax::

	&VDW_CORRECTION
	 DVDW [DVDW value]
	 S6   [S6 value]
	 CUTOFF [R1] [R2] [R3] 
	&END

  DVDW: d parameter in DFT-D2

  S6: s6 parameter in DFT-D2

  CUTOFF: Cutoff parameters in the directions of the first, second, and third lattice vectors.

&SYMM ... &END
 This block is used to set the symmetry manually.

  Syntax::
	
	&SYMM
	 NSPG
	 OP_NUM(1)
	 TAU(1)
	 OP_NUM(2)
	 TAU(2)
	 ...
	 OP_NUM(NSPG)
	 TAU(NSPG)
	&END

  NSPG: Number of symmetry operation

  OP_NUM(1:NSPG): Symmetry operation number (see opgr.f90)

  TAU(1:NSPG): Fractional translation associated with the symmetry operation.

&ESM ... &END
  This block specifies the parameters for the ESM calculation.

  Syntax::

	&ESM
	 BOUNDARY_CONDITION [boundary_condition]
	 Z1 [value]
	 CHARGE [value]
	 Z_WALL [value]
	 BAR_HEIGHT [value]
	 BAR_WIDTH [value]
	 ELECTRIC_FIELD [value]
	&END

  BOUNDARY_CONDITION: Boundary condition. Available options are BARE (PE0/BC1), PE1 (BC2), and PE2(BC3) for open (vacuum/slab/vacuum), metal/slab/metal, and vacuum/slab/metal boundary conditions, respectively

  Z1: Z position of the cell boundary

  CHARGE: Charge of the system. Note that positive value means deficit charge, while negative, excess charge.

  Z_WALL: Z position of an artifical wall potential for electron

  BAR_HEIGHT: Barrier height for the artifical wall potential for electron

  BAR_WIDTH: Width for the artifical wall potential for electron

  ELECTRIC_FIELD: Electric field (in Ha/Bohr) applied to the system. Use with the boundary condition PE1 (BC2).


&OCCUPATION ... &END
  This block is used to specify the occupations for the fixed occupation calculation (Gamma-point only).
  
&DOS ... &END
  This block is used to define the parameters needed to calculate DOS.

  EMIN: Minimum energy in eV.

  EMAX: Maximum energy in eV.

  NDOSE: Energy mesh for the density of states calculation.	

  EWIDTH: Smearing width for the Gaussian broadening 


&KPOINTS_BAND ... &END
  This block is used to define the parameters needed in the band structure calculation.

  NKSEG: Number of k-point segment for the band (the number of symmetry points should be NKSEG+1)

  KMESH: K-point mesh for each segment.

  KPOINTS: High symmetry k-points in the unit of the basic reciprocal lattice vectors (NKSEG+1 k-points should be specified).
  If 'KPOINTS CART' or 'KPOINTS CARTESIAN' is specified, they should be given in the unit of the cartesian coordinate.


&PLOT ... &END
 This block define the parameters needed in the wave function plot.

 IK/IKPT: K-point index at which the real-space wave functions are generated.

 IB: Band index at which the wave function is generated

 IBS/IBAND_S: The first band index for the wave function plot.

 IBE/IBAND_E: The last band index for the wave function plot (IBS-th to IBE-th wave functions at the IK k-point are generated). 

 FORMAT: Format of the wave function can be specified

 * STATE: STATE format (not yet implemented)

 * CUBE: Gaussian Cube format (default)

 * XSF: Xcryden Structure File

 * XSF_CHARGE/CHARGE_XSF: Charge densities corresponding to the specified wave functions in the Xcrysden Structure File format
 

.. warning::
	This document is by no means perfect.
