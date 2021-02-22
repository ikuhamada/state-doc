=============
Running STATE
=============

.. warning::
	This page is under construction

Having built it and obtained pseudopotentials, we are ready to run STATE!

Suppose the source directory is ``${HOME}/STATE/src/state/src`` and pseudopotentials are located in ``${HOME}/STATE/gncpp``, where $``${HOME}`` is the home directory.
In ``${HOME}/STATE``, let us create a directory for a test run for a CO molecule in a rectangular unit cell as

.. code:: bash

  $ mkdir -p test/CO; cd test/CO

Let us create symbolic link to a STATE command by executing

.. code:: bash

  $ ln -s ${HOME}/STATE/src/state-5.6.x/src/STATE

and those to pseudopotentials as

.. code:: bash

  $ ln -s ${HOME}/STATE/gncpp/pot.C_pbe1

  $ ln -s ${HOME}/STATE/gncpp/pot.O_pbe1

or

.. code:: bash

  $ ln -s ${HOME}/STATE/gncpp/C_pbe1/#vnew.data pot.C_pbe1

  $ ln -s ${HOME}/STATE/gncpp/O_pbe1/#vnew.data pot.O_pbe1

Then let us prepare the input file. Here we use the following file named ``nfinp_1``

.. code:: bash

  WF_OPT    DAV
  NTYP      2
  NATM      2
  GMAX      5.50
  GMAXP     20.00
  NSCF      200
  WAYMIX    3
  KBXMIX    8
  MIX_ALPHA 0.8
  WIDTH     0.0010
  EDELTA    0.1000D-09
  NEG       8
  CELL      6.00  4.00  4.00  90.00  90.00  90.00
  &ATOMIC_SPECIES
   C  12.011  pot.C_pbe1
   O  15.999  pot.O_pbe1
  &END
  &ATOMIC_COORDINATES
    0.0000  0.0000  0.0000  1  1  1
    2.2000  0.0000  0.0000  1  1  2
  &END

In the current working directory, let us execute::

  $ mpirun -np 6 ./STATE < nfinp_1 > nfout_1

where we use 2 processors and the output is written to ``nfout_1``. The MPI command depends on the system and a job script is necessary when we use a supercomputer facility.

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
   *              ******     ** VERSION 5.6.8  **    ********            *
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

This message is followed by the following lines, which show the convergence of the total energy (ETOTAL)::

   NSCF NADR            ETOTAL          EDEL          CDEL CONV      TCPU
      1    0      -16.71058056   0.16711E+02   0.89648E-01    0      0.06
      2    0      -20.04069483   0.33301E+01   0.63872E-01    0      0.05
      3    1      -21.45761599   0.14169E+01   0.68300E-01    0      0.05
      4    2      -22.15338988   0.69577E+00   0.28216E-01    0      0.05
      5    3      -22.21588778   0.62498E-01   0.76543E-02    1      0.05
      6    4      -22.21907373   0.31860E-02   0.18453E-02    1      0.05
      7    5      -22.21941896   0.34522E-03   0.49141E-03    2      0.05
      8    6      -22.21942378   0.48220E-05   0.10308E-03    2      0.05
      9    7      -22.21942425   0.46409E-06   0.15783E-04    3      0.05
     10    8      -22.21942426   0.98760E-08   0.48605E-05    3      0.05
     11    1      -22.21942426   0.29124E-09   0.22363E-05    3      0.05
     12    2      -22.21942425   0.62312E-09   0.30180E-05    3      0.05
     13    3      -22.21942426   0.99714E-09   0.79766E-06    3      0.05
     14    4      -22.21942426   0.72873E-10   0.58032E-07    4      0.05
     15    5      -22.21942426   0.11724E-12   0.20083E-07    5      0.05
     16    6      -22.21942426   0.85265E-13   0.69021E-08    6      0.05

When the SCF convergence is reached, total energy and its componets are printed as follows::

                       TOTAL ENERGY AND ITS COMPONENTS 
                    TOTAL ENERGY     =         -22.21942426 A.U.
                  KINETIC ENERGY     =           9.92111448 A.U.
                  HARTREE ENERGY     =           5.12121891 A.U.
                       XC ENERGY     =          -5.89585656 A.U.
                    LOCAL ENERGY     =         -20.23161767 A.U.
                 NONLOCAL ENERGY     =           6.73686187 A.U.
                    EWALD ENERGY     =         -17.87114528 A.U.
                       PC ENERGY     =           0.00000000 A.U.
                 ENTROPIC ENERGY     =           0.00000000 A.U.

Forces acting on atoms are::

      ATOM              COORDINATES                        FORCES
  MD:    1
  MD:    1  C   0.000000   0.000000   0.000000   0.01852  0.00000 -0.00000
  MD:    2  O   2.200000   0.000000   0.000000  -0.01858 -0.00000  0.00000

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
