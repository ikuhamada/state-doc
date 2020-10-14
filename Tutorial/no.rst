.. _tutorial_no:

:orphan:

============
Nitric oxide
============
This example explains how to perform a calculation of a system by taking spin polarization into account (see also atomization energy calculation of a hydrogen molecule) and examin if the system has a spin polarization.

SCF calculation with spin polarization
--------------------------------------
Below is an input file for a nitric oxide (NO) molecule in a box::

 WF_OPT    DAV
 NTYP      2
 NATM      2
 GMAX      6.0
 GMAXP     20.0
 MIX_ALPHA 0.3
 WIDTH     0.0010
 EDELTA    1.D-09
 NSPIN     2
 NEG       8 
 CELL   20.00000000  20.00000000  20.00000000  90.00000000  90.00000000  90.00000000
 &ATOMIC_SPECIES
  N    1.007940 pot.N_pbe1
  O    1.007940 pot.O_pbe1
 &END
 &INITIAL_ZETA
  0.20
  0.20
 &END
 &ATOMIC_COORDINATES CARTESIAN
       0.000000000000      0.000000000000      0.000000000000    1    1    1
       2.100000000000      0.000000000000      0.000000000000    1    1    2
 &END
  
Make sure to set non-zero initial spin polarization.
It is also noted that there are 2 atomic species and thus 2 initial spin polarizations (``ZETA1``) should be set as::

 &INITIAL_ZETA
  0.20
  0.20
 &END

Upon convergence, one finds the following in the output file::

                                      ALPHA SPIN DENSITY =      5.9999897
                                       BETA SPIN DENSITY =      4.9999944
                                    TOTAL CHARGE DENSITY =     11.0000159
 
                      TOTAL ENERGY AND ITS COMPONENTS 
                   TOTAL ENERGY     =         -26.30821655 A.U.
                 KINETIC ENERGY     =          11.41892451 A.U.
                 HARTREE ENERGY     =          27.07315959 A.U.
                      XC ENERGY     =          -6.34381088 A.U.
                   LOCAL ENERGY     =         -72.12366866 A.U.
                NONLOCAL ENERGY     =           7.92908549 A.U.
                   EWALD ENERGY     =           5.73809340 A.U.
                      PC ENERGY     =           0.00000000 A.U.
                ENTROPIC ENERGY     =           0.00000000 A.U.

We can see that the alpha (up) and beta (down) spin are 6.0 and 5.0, respectively, meaning that the system is spin polarized::

                                       ALPHA SPIN DENSITY =      5.9999897
                                        BETA SPIN DENSITY =      4.9999944
                                     TOTAL CHARGE DENSITY =     11.0000159

We can also find the eigenvalues and occupations below the total energy and Fermi level, which clearly indicate that 6 (5) electrons occupy alpha/up (beta/down) spin states as::

  NKP=    1  NGP=     29039  K=(  0.00000  0.00000  0.00000)  WKP= 0.5000
                               EIGEN VALUE 
  -1.19024 -0.60659 -0.48880 -0.48534 -0.42606 -0.14951 -0.13615 -0.01025
                                OCCUPATION 
   1.00000  1.00000  1.00000  1.00000  1.00000  1.00000  0.00000  0.00000
  NKP=    2  NGP=     29039  K=(  0.00000  0.00000  0.00000)  WKP= 0.5000
                               EIGEN VALUE 
  -1.17319 -0.57956 -0.47617 -0.43755 -0.40540 -0.12202 -0.07752 -0.00580
                                OCCUPATION 
   1.00000  1.00000  1.00000  1.00000  1.00000  0.00000  0.00000  0.00000

Furthermore, local atomic charges are printed as follows::

            <<<  Atomic Charge >>>
   ia is   rd d_rd  Charge(1)  Charge(2)  Charge(3)
    1  1 1.40 0.10   1.703104   1.929256   2.151185
    1  2 1.40 0.10   1.329765   1.522052   1.713526
    2  1 1.40 0.10   2.251678   2.475492   2.683927
    2  2 1.40 0.10   2.001271   2.209236   2.403069

The first, second, third, and forth column indicate atomic index (ia), spin state (is, 1 and 2 are for spin-up and spin-down, respectively), radius for the integration (rd), and increment of the radius (d_rd), respectively, and the following columns are the integrated charges within the radii.
In this example the charges within the 1.40, 1.50, and 1.60 Bohrs are printed.
Likewise, the local magnetic moments are also printed::
 
            <<<  Magnetization >>>
   ia      rd d_rd  magmom(1)  magmom(2)  magmom(3)
    1    1.40 0.10   0.373340   0.407204   0.437658
    2    1.40 0.10   0.250407   0.266256   0.280858

