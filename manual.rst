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

	* FIRE: Fast Inertial Relaxation Engine (original)

	* FIRE_OLD|FIRE_IH: Fast Inertial Relaxation Engine (old implementation by Hamada)

	* FIRE2|FIRE2.0: Fast Inertial Relaxation Engine 2.0

	* NEB: Nudged elastic band method to find saddle points and minimum energy paths

	* CINEB: Climbing-image NEB method (this keyword should be used only for the image to be climed or that at the transision state, not all the images)


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
.. warning::
	Be aware that using the keyword ``RESTART`` and ``ICOND`` may result in a conflict. It is recommended `not` to use these keywords at the same time. Also, ``RESTART`` and ``TASK`` cannot be used at the same time. See the ``TASK`` section for restart options.


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

	Use this keyword to print the charge density in real space.


DOS
	Type: character

	Default: none

	Description:

	Use this keyword to print the total density of states.


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

	Use this keyword to generate data for the COOP analysis.


BAND
	Type: character

	Default: none

	Description:

	Use this keyword to perform the band structure analysis.


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

	* RESTART_SCF | RESTART_WF_OPT : Restarting the previous SCF calculation

	* NSCF : Non-SCF calculation

	* BAND : Band structure calculation

	* OPT | GEO_OPT : Structural optimization

	* RESTART_OPT | RESTART_GEO_OPT : Restarting the previous structural optimization

	* MD | FTMD : Finite temperature molecular dynamics (FTMD)

	* RESTART_MD | RESTART_FTMD : Restarting the previous FTMD simulation

	* ZTMD : Zero temperature molecular dynamics (ZTMD)

	* RESTART_ZTMD: Restarting the previous ZTMD simulation

	* NEB : Nudged elastic band (NEB) calculation

	* RESTART_NEB : Restarting the previous NEB calculation

	* CINBE : Climbing-image nudged elastic band (CINEB) calculation

	* RESTART_CINEB: Restarting the previous CINEB calculation

	* VIB : Vibrational mode analysis

	* RESTART_VIB: Restarting the previous vibrational mode analysis

	* VIB_DPL: Calculate and print the dipole moments in the z-direction at given atomic displacements

	* RESTART_VIB_DPL: Restartin the previous calculations of the dipole moments in the z-direction at given displacements

	* PRTRHO | PRTCHG : Print the charge density in real space

	* DOS : Print the total density of states

	* PDOS | AOLDOS : Print the density of states projected onto atomic orbital (AOLDOS)

	* PRTWFC | PRTWFN : Print wave function(s) in real space

	* PRTWFC_BAND | PRTWFN_BAND : Print wave function(s) in real space

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

        Following space group numbers are used for 2D systems.

        * 1001: *p1*

        * 1002: *p2*

        * 1003: *p1m1*

        * 1004: *p1g1*

        * 1005: *c1m1*

        * 1006: *p2mm*
       
        * 1007: *p2mg*

        * 1008: *p2gg*

        * 1009: *c2mm*

        * 1010: *p4*

CELL
	Type: real array

	Default: 0.0 0.0 0.0 0.0 0.0 0.0

	Description:

	Lengths of first, second, and third vectors (A, B, and C), and angles (in degree) between, second and third, third and first, and first and second vectors (ALPHA, BEGA, GAMMA).
        These parameters define the basic lattice vectors of the *conventional* unit cell and the lattice vectors of the  *primitive* lattice vectors used in the actual calculation depends on ``BRAVIS_TYPE`` or ``TYPE``.
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

INITIALIZE
	Type: character

	Default: none

	Description:

	Initialization

	* WF: Wave functions are initialized (``ICOND=0``)

	* POS: Atomic positions are read from the input file (``INIPOS=0``)

	* VEL: Velocity is initialized (``INIVEL=0``)

	* NOSE: Nose variables are initialized (``ININOS=0``)

	* ACC: Accumulators are initialized (``INIACC=0``)

NSCF
	Type: integer
	
	Default: 200

	Description: 

	Number of maximum SCF steps.

NSTEP
	Type: integer
	
	Default: 200

	Description:

	Number of maximu ionic steps.

CPUMAX
	Type: real
	
	Default: none

	Description:

	Max. CPU time in second.

WAY_MIX | WAYMIX
	Type: integer

	Default: 6

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

	* DFP: DFP mixing

	* PULAY: Pulay mixing

	* BLUGEL: Bluegel-Ishida mixing scheme 

MIXOBJ
	Type: character

	Default: CHARGE

	Description:

	Mixing object.

	* CHARGE: charge density

	* POTENTIAL: potential


KBXMIX | NMIX
	TYpe: integer

	Default: 30

	Description:

	Number of charges/potentials to be stored for the mixing. After ``KBXMIX`` iteration, the mixing information is reset.


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

	Convergence threshold (Hartree/atom) for the total energy.


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

	* vdw-df-cx/bh (vdW-DF) of Berland and Hyldgaard

NSPIN
	Type: integer
	
	Default: 1

	Description:

	Number of spin component.

	* 1: spin unpolarized case

	* 2: spin polarized case

SPIN
	type: character

	Default: none

	Description:

	Spin multiplicity. When this variable is used, the fixed spin moment calculation is performed. The allowed muliplicities using this keyword are singlet, doublet, triplet, ..., and octet.

SPIN_MULTIPLICITY
	type: integeger

	Default: none

	Description: Spin multiplicity. When this variable is used, the fixed spin moment calculation is performed.

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

	This keyword defines the ensemble method for the finite temperature molecular dynaics simulation.

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

	Integer to define the method of velocity control for the finite temperature molecular dynamics simulation.

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

	Tolerance of temperature in Kelvin. This variable is used in the simple velocity rescaling or rolling average method.


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
	
	Friction coefficient used to generage random forces for Langevin molecular dynamics.

CHARGE
	Type: real

	Default: 0.D0

	Description:

	Charge of the system. Positive (negative) value indicates the system has deficit (excess) electron(s).

VERBOSITY
	Type: character

	Default: LOW

	Description:

	Output level.

	* LOW: minimum output

	* MEDIUM: standard level of output (as in the legacy STATE with IPRI=1)

	* HIGH: more output (for debugging)

	The variable ``IPRI`` can be used to control the output level as:

	* IPRI < 0: minimum output level

	* IPRI = 1: standard output level

	* IPRI > 1: more output level 

NNEB
	Type: integer

	Default: 0

	Description:

	The number of standard NEB steps before the climbing-image NEB calculation.
	
VERBOSITY_NEB
	Type: character

	Default: LOW

	Description:

	Output level for the NEB calculation.

	* LOW: minimum output

	* HIGH: more output (for debugging)

PRTCHGPRO | PRT_CHGPRO | PRINT_CHGPRO
	Type: character

	Default: ON

	Description:

	Output level for the charge profile.

	* OFF: No output

	* ON: Minimum output

	* ALL|EVERY_STEP: Output the charge profile at every step

PRTELE | PRT_ELE | PRINT_ELE
	Type: character

	Default: none

	Description:

	Output level for the wave functions and charge density /potential.

	* OFF: No output

	* ON: Minimum output (at the end of SCF/structural optimization steps)

	* ALL | EVERY_STEP: Output wave functions and charge density / potential at every structural optimization / molecular dynamics steps

NSTEPS_PRINT_ELE
	Type: integer

	Default: 0

	Description:

	Frequency of the wave function/charge density/potntial output. They are printed out every ``NSTEP_PRINT_ELE`` steps and if negative, they are not printed at all.

GNCPP_DIR | GNCPPDIR
	Type: character

	Default: "."

	Description:

	GNCPP (pseudopotential) directory

OUT_DIR | OUTDIR
	Type: character

	Default: "."

	Description:

	Full path to the output directory (default: "." means the directory where the STATE executable is located).

ESM | ESM_BC
	Type: character

	Default: none

	Description:

	This keyword activate the effective screening medium (ESM) method and specify the periodic boundary condition used.

	* BC1 | PE0 | BARE: Vacuum/slab/vacuum boundary condition (Bare Coulomb)

	* BC2 | PE1: Metal/slab/metal boundary condition

	* BC3 | PE2: Vacuum/slab/metal boundary condition

	* BC4 | PE3: Vacuum/slab/metal boundary condition (smooth ESM)

ESM_Z1
	Type: real

	Default: c / 2 (c is the length of the unit cell vector in the surface normal direction)

	Description:

	Z-coordinate of the boundary between vacuum and ESM.

ESM_E_FIELD | ESM_EFIELD | ESM_ELECTRIC_FIELD  
	Type: real

	Default: none

	Description:

	Electric field used with BC2 and BC3 of the ESM method in Hartree/Bohr.
	``E_FIELD`` can also be used.

ESM_E_FIELD_EVA | ESM_EFIELD_EVA | ESM_ELECTRIC_FIELD_EVA
	Type: real

	Default: none

	Description:

	Electric field used with BC2 BC3 of the ESM method in eV/Angstrom.
	``E_FIELD_EVA`` can also be used.

ESM_NEW_EWALD
	Type: none

	Default: none

	Description:

	An alternative implementation of the Ewald method. Try this option when the system is highly anisotoropic.

STMOPT
	Type: integer

	Default: none

	Description:

	An integer to specify how to reconstruct the wave function in the vacuum region for an STM simulation.

	* 0: No wave function reconstruction

	* 1: Reconstruction of wave functions so that they decay exponentially in the vacuum region.

	* 2: Reconstruction of wave functions by solving them using the planar average electrostatic potential in the vacuum region (experimental).

DESTM | BIAS | STM_BIAS
	Type: real

	Default: 0

	Description:

	STM bias in eV.

Z0STM | Z0_STM | STM_Z0
	Type: real

	Default: none

	Description:

	Z-coordinate (in Bohr) at which the charge density is negligiblly small in the vacuum region. Used for STM simulations (``STMOPT>0``)

VAC | STM_VAC | VACUUM_LEVEL
	Type: real

	Default: none

	Description:

	Vacuum level used for STM simulations.

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

  ALFA: Initial charge (obsolete)

  AMION: Atomic weight in atomic mass unit

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

	&ATOMIC_COORDINATES [CRYSTAL|CRYS|CARTESIAN|CART|CONVENTIONLAL|CONV]
	 CPS(1,1) CPS(1,2) CPS(1,3) IWEI(1) IMDTYP(1) ITYP(1)
	 CPS(2,1) CPS(2,2) CPS(2,3) IWEI(2) IMDTYP(2) ITYP(2)
	 ...
	 CPS(NATM,1) CPS(NATM,2) CPS(NATM,3) IWEI(NATM) IMDTYP(NATM) ITYP(NATM)
	&END
	
	
  CARTESIAN/CART: If set, atomic coordinates are given in the cartesian coordinate

  ANGSTROM: If set, atomic coordinates are given in Angstrom (cartesian)

  CRYSTAL/CRYS: If set, atomic coordinates are given in the crystal coordinate

  CONVENTIONLAL|CONV: If set, atomic coordinates are given in the unit of the conventional lattice vectors

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

.. warning::

  If ``CRYSTAL``, ``CARTESIAN``, or ``CONVENTIONAL`` is specified in the &ATOMIC_COORDINATES ... &END block and at the same time ``NCORD`` or ``CORD`` is also used, the latter is overwritten. Do not use these options together.


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


&PDOS ... &END | &AOLDOS ... &END
  This block is used to define the parameters needed to calculated PDOS (AOLDOS) in the legacy STATE format.

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
         GRIMME
	 DVDW [DVDW value]
	 S6   [S6 value]
	 CUTOFF [R1] [R2] [R3] 
	&END

  GRIMME/DFT-D2/DFTD2: The method of the dispersion correction. Only these options (Grimme's DFT-D2) are available.

  DVDW: d parameter in DFT-D2 (default: 20)

  S6: s6 parameter in DFT-D2 (default: 0.75 for PBE/RPBE/revPBE)

  CUTOFF: Cutoff parameters in the directions of the first, second, and third lattice vectors (default: 0 (no supercell))

  DEBUG/VERBOSE/VERBOSE_OUTPUT: verbose output for the van der Waals correction 

&VDW-DF ... &END
 This block is used to set the option(s) for the vdW-DF calculation.

  Syntax::

	&VDW-DF
	 SVDW-DF | NON-SVDW-DF 
         QCUT [value]
         NQ   [value]
	&END

  SVDW-DF | NON-SVDW-DF: Keyword to set svdW-DF [default for nspin=1 (nspin=2): NON-SVDW-DF (SVDW-DF)]

  QCUT: cutoff for the q0 function (default: 10.0)

  NQ: grid for the q0 (default: 20)


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

  CHARGE: Charge of the system. Note that positive value means deficit charge, while negative, excess charge

  Z_WALL: Z position of an artifical wall potential for electron

  BAR_HEIGHT: Barrier height for the artifical wall potential for electron

  BAR_WIDTH: Width for the artifical wall potential for electron

  ELECTRIC_FIELD: Electric field (in Ha/Bohr) applied to the system. Use with the boundary condition PE1 (BC2)


&FIRE ... &END
  This block is used to set the parameters for the FIRE method

  Syntax::

	&FIRE
	&END

  NMIN: Minimum number of steps when P > 0 (default: 5)

  F_INC: Factor to increase the time step (default: 1.1)

  F_DEC: Factor to decrease the time step (default: 0.5)

  ALPHA_START: Mixing parameter for the velocity and its starting value (default: 0.1)

  F_ALPHA: Factor to decrease the mixing parameter alpha (default: 0.99)

  DTIO_MAX: Maximum time step (default: 20 atomic unit)


&OCCUPATION ... &END
  This block is used to specify the occupations for the fixed occupation calculation (Gamma-point only).

  Syntax (nspin=1)::

	&OCCUPATION
	 [OCC(1)] [OCC(2)] ... [OCC(N)]
	&END

  Syntax (nspin=2)::

	&OCCUPATION
	 [OCC(1)] [OCC(2)] ... [OCC(Nup)]
	 [OCC(1)] [OCC(2)] ... [OCC(Ndw)]
	&END

  where OCC(n) is the occupation of the n-th band.


&FIXED_MOMENT (&SPIN) ... &END 
  This block is used to activate the fixed spin moment calculation and to specify the spin multiplicity

  Syntax (A)::

	&FIXED_MOMENT
	 SPIN_MULTIPLICITY [value]
	&END

  The value is the integer, which specifies the spin multiplicity. For instance, use 1 for singlet and use 3 for triplet.

  Syntax (B)::

	&FIXED_MOMENT
	 SPIN [SINGLET|DOUBLET|TRIPLET|...|OCTET]
	&END

  Syntax (C)::

	&FIXED_MOMENT
	 MOMENT [value]
	&END

  The value is a real number, which specifies the magnetic (spin) moment of the system.
  

&DOS ... &END
  This block is used to define the parameters needed to calculate DOS.

  Syntax::

	&DOS
	 EMIN [value]
	 EMAX [value]
         NDOSE [value]
         EWIDTH [value]
	&END

  EMIN: Minimum energy in eV (default: -0.5 Hartree ~ -13.6 eV)

  EMAX: Maximum energy in eV (default: 0.3 Hartree ~ 8.2 eV)

  NDOSE: Energy mesh (integer) for the density of states calculation (default: 2000)

  EWIDTH: Smearing width for the Gaussian broadening in eV (default: 0.01 Hartree ~ 0.3 eV)


&ALDOS ... &END
  This block is used to define the parameters needed to calculate atomic layer resolved DOS (ALDOS).

  Syntax::

	&ALDOS
	 ZMIN [value]
	 ZMAX [value]
	 NLAY [value]
	 EMIN [value]
	 EMAX [value]
         NDOSE [value]
         EWIDTH [value]
	&END

  ZMIN: Minimum z-position for ALDOS in Bohr
  
  ZMAX: Maximum z-position for ALDOS in Bohr

  NLAY: Number of atomic layers to be considered between `ZMIN` and `ZMAX`

  EMIN: Minimum energy in eV (default: -0.5 Hartree ~ -13.6 eV)

  EMAX: Maximum energy in eV (default: 0.3 Hartree ~ 8.2 eV)

  NDOSE: Energy mesh (integer) for the density of states calculation (default: 2000)

  EWIDTH: Smearing width for the Gaussian broadening in eV (default: 0.01 Hartree ~ 0.3 eV)


&KPOINTS_BAND ... &END
  This block is used to define the parameters needed in the band structure calculation.

  Syntax::

	&KPOINTS_BAND
	 NKSEG [value]
	 KMESH [value1] [value2] ... [valueN]
	 KPOINTS
	 [kx1] [ky1] [kz1]
	 [kx2] [ky2] [kz2]
	        ...
	 [kxN] [kyN] [kzN]
	&END

  NKSEG: Number of k-point segment for the band (the number of symmetry points should be NKSEG+1)

  KMESH: K-point mesh for each segment.

  KPOINTS: High symmetry k-points in the unit of the basic reciprocal lattice vectors (NKSEG+1 k-points should be specified).
  If 'KPOINTS CART' or 'KPOINTS CARTESIAN' is specified, they should be given in the unit of the cartesian coordinate.


&PLOT ... &END
  This block define the parameters needed in the wave function plot.

  Syntax::

	&PLOT
	 IKPT [value]
	 IB [value]
	 [CHG_WFN]
	 [ADD_SIGN]
         [PRT_VLOC]
	 FORMAT [value]
	&END

  IK/IKPT: K-point index at which the real-space wave functions are generated (default: 1)

  IB: Band index at which the wave function is generated (default: 1)

  IBS/IBAND_S: The first band index for the wave function plot (default: 1)

  IBE/IBAND_E: The last band index for the wave function plot (default: 1: IBS-th to IBE-th wave functions at the IK k-point are generated)

  CHG_WFN/CHG_WFC: Calculate the wave function densities

  ADD_SIGN/ADD_SIGN_MO_DEN/ADD_SIGN_WF_DEN: Option to add the sign to the wave function densities. Valid only for the wave functions at the Gamma point.

  FORMAT: Format of the wave function can be specified

  * STATE: STATE format (not yet implemented)

  * CUBE: Gaussian Cube format (default)

  * XSF: Xcryden Structure File

  * XSF_CHARGE/CHARGE_XSF: Charge densities corresponding to the specified wave functions in the Xcrysden Structure File format

  PRTVLOC/PRT_VLOC/PRINT_VLOC: Local potential (sum of the local and Hartree potentials) in the Xcrysden Structure File format

&VIBRATION ... &END
  This block is used to set parameters for the finite difference method.

  Syntax::

	&VIBRATION
	 DISP [value]
	 ATOM [valueN1]-[valueN2]
	&END

  DISP/DISPLACMENT: Displacement (default: 0.02 Bohr)

  ATOM: Used to specify the atoms to be displaced (default: 1-N, where N is the number of atoms)

&COOP ... &END
  This block is used to specify the parameters for the COOP analysis (prep for the COOP analysis by using the ``coop_analysis`` program) when ``TASK COOP`` is set. 

  Syntax::

	&COOP
	 KPDOSMO_MOL1 [value]
	 KPDOSMO_MOL2 [value]
	 KPDOSMO_SUB  [value]
	 KATM_MOL1    [value]
	 KATM_MOL2    [value]
	 KATM_SUB     [value]
	 KLMTA_MOL1   [value]
	 KLMTA_MOL2   [value]
	 KLMTA_SUB    [value]
	 WFN_MOL1     [value]
	 WFN_SUB      [value]
	&END

  KPDOSMO_MOL1: Number of bands (MOs) for the molecule #1 used in the COOP analysis

  KPDOSMO_MOL2: (optional) Number of bands (MOs) for the molecule #2 used in the COOP analysis

  KPDOSMO_SUB: Number of bands for the substrate used in the COOP analysis

  KATM_MOL1: Number of atoms for the molecule #1 

  KATM_MOL2: (optional) Number of atoms for the molecule #2

  KATM_SUB: Number of atoms for the substrate

  KLMTA_MOL1: Number of projectors (l, m, tau) for the molecule #1 (search KLMTA in calculation of the sub system)

  KLMTA_MOL2: (optional) Number of projectors (l, m, tau) for the molecule #2 (search KLMTA in calculation of the sub system)

  KLMTA_SUB: Number of projectors (l, m, tau) for the substrate (search KLMTA in calculation of the sub system)

  WFN_MOL1: Wave function file (zaj.data) for the molecule #1 (default: zak1.data)

  WFN_MOL2: (optional) Wave function file (zaj.data) for the molecule #2 (default: zak2.data)

  WFN_SUB: Wave function file (zaj.data) for the substrate (default: zak3.data)


&OTHERS ... &END
  This block is used to set other parameters

  GAUSSDOS: Density of states is calculated by using the Gaussian smearing (default: unset)

  PRTCHGPRO: IF OFF, the charge profile is disabled (default: ON)
 

.. warning::
	This document is by no means perfect.
