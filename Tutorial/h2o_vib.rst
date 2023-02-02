.. _tutorial_h2o_vib:

:orphan:

Water
=====
This example explains how to perform the vibrational mode analysis using the finite different method and how to refine it . We use a water molecule in a box as an example.

First vibrational mode analysis
-------------------------------

First we perfom a series of SCF calculations by displacing the atoms in each cartesian direction. In the legacy STATE code, we needed to prepare a ``nfvibrate.data`` file to define the atomic displacement, but it is automatically generated (default displacement is 0.01 Bohr). Following is the input file (``nfinp_vib_1``)::

  TASK       VIB
  WF_OPT     DAV
  FMAX       1.D-3
  DTIO       200.00
  NTYP       2
  NATM       3
  GMAX        6.00
  GMAXP      20.00
  MIX_ALPHA   0.5
  EDELTA      1.D-10
  NEG        12
  CELL       15.00 15.00 15.00  90.00  90.00  90.00
  &ATOMIC_SPECIES
   H    1.00797 pot.H_pbe1
   O   15.99940 pot.O_pbe1
  &END
  &ATOMIC_COORDINATES CARTESIAN
        1.453447222619      0.000000000000      1.124989276510    1    1    1
       -1.453447222619      0.000000000000      1.124989276510    1    1    1
        0.000000000000      0.000000000000      0.000000000000    1    1    2
  &END
  &VIBRATION
   DISP 0.02
  &END

We use the option::

  TASK       VIB

to perform the vibrational analysis. If you want to change the displacement use the following option::

  &VIBRATION
   DISP 0.02
  &END

By running STATE, you may find ``nfforce.data`` in the working directory, which contains the data of displacements and forces. If the calculation is not interrupted, it should contain 6 times N displacement and force data, where N is the number of atoms.

.. warning::
        Displacements and forces are appended when ``nfforce.data`` exists. Rename the existing ``nfforce.data`` file, if you do not want to.

To obtain the vibrational frequencies and modes, use ``gif`` as follows:

.. code:: bash

  $ gif -f nfforce.data > gif.out_1

In the present case, vibrational frequencies are printed like::

                   =========             
                    SUMMARY              
                   =========             
  
   MODE  WR           : NU(meV)  NU(cm-1)
      1 -0.161221D-03 :    8.06     65.03
      2 -0.127681D-04 :    2.27     18.30
      3  0.973343D-05 :    1.98     15.98
      4  0.144401D-04 :    2.41     19.46
      5  0.575098D-04 :    4.82     38.84
      6  0.141208D-03 :    7.55     60.86
      7  0.940090D-01 :  194.71   1570.43
      8  0.525214D+00 :  460.23   3711.95
      9  0.556815D+00 :  473.87   3821.99


and the vibrational modes are printed in ``vib.data``


Refining the vibrational frequencies and modes
----------------------------------------------

To check if the displacement is small enough (so that we obtain the harmonic vibrational frequencies, we usually change the displacement in the cartesian directions and repeat the calculations. Rather, we perform the following calculation(s). Instead of using the cartesian coordinate, we generate new displacements using the vibrationa mode (eigenmode) obtained in the previous step. That is, the dynamical matrix is now constructed using the eigenmode as a basis. We first rename ``vib.data`` ``vib.data_1`` (``nfforce.data`` ``nfforce.data_1`` and ``nfvibrate.data`` ``nfvibrate.data_1``) and execute ``duplicate`` as

.. code:: bash

  $ duplicate vib.data_1 nfvibrate.data

Then the similar input file (``nfinp_vib_2``) to the first one is used to perform a new set of the calculations::

  TASK       VIB
  WF_OPT     DAV
  NTYP       2
  NATM       3
  GMAX        6.00
  GMAXP      20.00
  MIX_ALPHA   0.5
  EDELTA      1.D-10
  NEG        16
  CELL       15.00 15.00 15.00  90.00  90.00  90.00
  &ATOMIC_SPECIES
     H    1.00797 pot.H_pbe1
     O   15.99940 pot.O_pbe1
  &END
  &ATOMIC_COORDINATES CARTESIAN
        1.453447222619      0.000000000000      1.124989276510    1    1    1
       -1.453447222619      0.000000000000      1.124989276510    1    1    1
        0.000000000000      0.000000000000      0.000000000000    1    1    2
  &END

and run ``gif`` after finishing the second STATE run as:

.. code:: bash

  $ gif -f nfvibrata.data > gif.out_2

and obtain the following vibrational frequencies::

                   =========             
                    SUMMARY              
                   =========             
  
   MODE  WR           : NU(meV)  NU(cm-1)
      1 -0.127899D-03 :    7.18     57.93
      2 -0.105889D-04 :    2.07     16.67
      3 -0.238793D-05 :    0.98      7.91
      4  0.198919D-02 :   28.32    228.44
      5  0.392124D-02 :   39.77    320.73
      6  0.439408D-02 :   42.10    339.52
      7  0.940996D-01 :  194.80   1571.19
      8  0.525102D+00 :  460.18   3711.56
      9  0.556590D+00 :  473.77   3821.22

We can see that the high-frequency modes are almost unchanged, confirming the finite difference calculation with the cartesian displacements.

It may be interesting to compare the dynamical matrices obtained in the first and second steps. In the first calculation, the symmetrized 9 times 9 dynamial matrix looks::

      0.355 -0.000  0.222 -0.030  0.000 -0.030 -0.325 -0.000 -0.193
     -0.000  0.000 -0.000  0.000  0.000 -0.000 -0.000  0.000  0.000
      0.222 -0.000  0.204  0.030  0.000  0.009 -0.252 -0.000 -0.212
     -0.030  0.000  0.030  0.355 -0.000 -0.222 -0.325  0.000  0.193
      0.000  0.000  0.000 -0.000  0.000  0.000 -0.000  0.000  0.000
     -0.030 -0.000  0.009 -0.222  0.000  0.204  0.252 -0.000 -0.212
     -0.325 -0.000 -0.252 -0.325 -0.000  0.252  0.651  0.000  0.000
     -0.000  0.000 -0.000  0.000  0.000 -0.000  0.000 -0.000  0.000
     -0.193  0.000 -0.212  0.193  0.000 -0.212  0.000  0.000  0.424

On the other hand, the dynamical matrix obtained in the second calculation is::

      0.016 -0.000  0.000  0.000  0.000 -0.006 -0.000  0.000 -0.000
     -0.000  0.005  0.000  0.000 -0.000  0.000  0.000 -0.000 -0.001
      0.000  0.000  0.002 -0.001 -0.000 -0.000  0.000 -0.000 -0.000
      0.000  0.000 -0.001  0.000  0.000 -0.000  0.000 -0.000 -0.000
      0.000 -0.000 -0.000  0.000 -0.000 -0.000 -0.000 -0.000  0.000
     -0.006  0.000 -0.000 -0.000 -0.000  0.002 -0.000  0.000 -0.000
     -0.000  0.000  0.000  0.000 -0.000 -0.000  0.154 -0.000 -0.000
      0.000 -0.000 -0.000 -0.000 -0.000  0.000 -0.000  0.868  0.000
     -0.000 -0.001 -0.000 -0.000  0.000 -0.000 -0.000  0.000  1.171

We can see that it is almost diagonal, meaning that the basis used indeed diagonalizes the dynamical matrix. By repeating this process, we can obtain the basis (eigenvectors) which fully diagonalizes the dynamical matrix.

