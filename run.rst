=============
Running STATE
=============

.. warning::
	This page is under construction

Having built it and obtained pseudopotentials, we are ready to run STATE!

Suppose the source directory is ``${HOME}/STATE/src/state/src`` and pseudopotentials are located in ``${HOME}/STATE/gncpp``.
In ``${HOME}/STATE``, let us create a directory for a test run for a CO molecule in a rectangular unit cell as::

  mkdir -p test/CO; cd test/CO

Let us create symbolic link to a STATE command by executing

.. code:: bash

  $ ln -s ${HOME}/STATE/src/state/src/STATE

and those to pseudopotentials as

.. code:: bash

  $ ln -s ${HOME}/STATE/gncpp/pot_C_pbe1 fort.37

  $ ln -s ${HOME}/STATE/gncpp/pot_O_pbe1 fort.38

or

.. code:: bash

  $ ln -s ${HOME}/STATE/gncpp/C_pbe1/#vnew.data fort.37

  $ ln -s ${HOME}/STATE/gncpp/O_pbe1/#vnew.data fort.38

Then let us prepare the input file. Here we use the following file named ``nfinp_1``

.. code:: bash

  NTYP      2
  NATM      2
  TYPE      0
  GMAX      5.50
  GMAXP     20.00
  NCORD     1
  NSCF      200
  WAYMIX    3
  MIX_WHAT  1
  KBXMIX    8
  MIX_ALPHA 0.8
  WIDTH     0.0010
  EDELTA    0.1000D-09
  NEG       8
  &ATOMS
   6.00  0.1500  51577.50 3 1  0.0000
   8.00  0.1500  51577.50 3 1  0.0000
  &END
  &CELL
    6.0000  4.0000  4.0000  90.000  90.000  90.000
  &END
  &ATOMIC_COORDINATES
    0.0000  0.0000  0.0000  1  1  1
    2.2000  0.0000  0.0000  1  1  2
  &END

In the current working directory, let us execute::

  mpirun -np 2 ./STATE < nfinp_1 > nfout_1

where we use 2 processors and the output is written to ``nfout_1``. The MPI command depends on the system and a job script is necessary when we use a supercomputer fascility.

In this example, only the single-point (or SCF) calculation is performed and no structural optization is performed.

Once your job starts, the following greeting is printed in ``nfout_1``::

   ***********************************************************************
   *                                                                     *
   *                                                                     *
   *                                                                     *
   *              ******  ********    **    ******** ********            *
   *             ******** ********   ****   ******** ********            *
   *             **          **     **  **     **    **                  *
   *              ***        **    ********    **    ******              *
   *                ***      **   **********   **    ******              *
   *                  **     **  **        **  **    **                  *
   *             ********    ** **          ** **    ********            *
   *              ******     ** VERSION 5.6.5  **    ********            *
   *                               RICS-AIST                             *
   *                           OSAKA UNIVERSITY                          *
   *                                                                     *
   ***********************************************************************

and the following when the SCF starts::

   ***********************************************************************
   *                                                                     *
   *                              START SCF                              *
   *                                                                     *
   ***********************************************************************

The convergence of the total energy can be monitored by executing

.. code:: bash

  grep ETOT\: nfout

and we get the following::

  ETOT:   1    -16.71058056  0.1671E+02  0.8965E-01
  ETOT:   2    -20.04069483  0.3330E+01  0.6387E-01
  ETOT:   3    -21.96017776  0.1919E+01  0.4847E-01
  ETOT:   4    -22.11633389  0.1562E+00  0.3198E-01
  ETOT:   5    -22.20286500  0.8653E-01  0.1510E-01
  ETOT:   6    -22.21912414  0.1626E-01  0.3085E-02
  ETOT:   7    -22.21938566  0.2615E-03  0.7750E-03
  ETOT:   8    -22.21941988  0.3422E-04  0.2094E-03
  ETOT:   9    -22.21942413  0.4249E-05  0.4735E-04
  ETOT:  10    -22.21942395  0.1857E-06  0.4811E-04
  ETOT:  11    -22.21942422  0.2798E-06  0.1838E-04
  ETOT:  12    -22.21942425  0.2761E-07  0.6088E-05
  ETOT:  13    -22.21942426  0.3338E-08  0.3279E-06
  ETOT:  14    -22.21942426  0.8036E-11  0.8071E-07
  ETOT:  15    -22.21942426  0.1084E-11  0.1565E-07
  ETOT:  16    -22.21942426  0.3197E-13  0.7047E-08

When the SCF convergence is reached, total energy and its componets are printed as follows::

                       TOTAL ENERGY AND ITS COMPONENTS 
                    TOTAL ENERGY     =         -22.21942426 A.U.
                     FREE ENERGY     =         -22.21942426 A.U.
                  KINETIC ENERGY     =           9.92111448 A.U.
                  HARTREE ENERGY     =           5.12121891 A.U.
                       XC ENERGY     =          -5.89585656 A.U.
                    LOCAL ENERGY     =         -20.23161767 A.U.
                 NONLOCAL ENERGY     =           6.73686187 A.U.
                    EWALD ENERGY     =         -17.87114528 A.U.
                       PC ENERGY     =           0.00000000 A.U.
                 ENTROPIC ENERGY     =           0.00000000 A.U.

Forces acting on atoms::

      ATOM              COORDINATES                        FORCES
  MD:   1
  MD:     1  C    0.000000    0.000000    0.000000   0.01852  0.00000 -0.00000
  MD:     2  O    2.200000    0.000000    0.000000  -0.01858 -0.00000  0.00000

And the "victory cats" at the bottom of the output file::

   HHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH
   HHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH
                             _______________________
       __________   _______/______v______v______v___]
      D          | |                                 |
      D   A A    | | Congratulations!                |  C( > < )D
    --  =(^.^)=  | |  The calculation has converged. |    = o =
   |     @@@@@   | |                                 |    (    )~
   /--=O=-+-=O=---+--=O=--+--==O==--+--==O==--+--=O=-+--=O=---=O=-/
    
   HHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH
   HHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH

If the convergence is not achieved, you will see the followinng::

   Sorry!                                           < < <  
     The calculation has not converged.            < < <   
                                                     < < <  
                                              ___________________
     @ @                                     |                   |
      *    ***                               |                   |XXX
      *   *   *   *                          |   Have a break!   |   X
       ***     ***  ...                      |                   |   X
                                             |                   |   X
                                             |                   |XXX
                 @@                          |___________________|
                  ***** ...                [_______________________]
  
Then take a break, optimize your convergence parameters (mixing parameter, mixing scheme), and restart the calculation.
