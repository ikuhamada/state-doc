============================
Compilation and installation
============================

.. warning::
	This page is under construction

Obtaining the code
==================

The code and pseudopotentials can be obtained upon request to the STATE developers.

Platform specific information can be found by following :any:`this link <platform>`.

Prep
====

Let us first make the root directory for the STATE. In the home directory, type

.. code:: bash

  $ mkdir STATE

Go to the STATE directory and create a directory as

.. code:: bash

  $ cd STATE
   
.. code:: bash

  $ mkdir gncpp

Pseudopotentials are stored in ``gncpp``.
Obtain a set of pseudopotentials (usually named as ``gncpp.tgz``) and unpack it under ``gncpp``
Then create a source directory as

.. code:: bash

    $ mkdir src

Compilation
===========

Having obtained the source code, say ``state-5.6.6.tgz``, unpack the source code under ``src`` as

.. code:: bash

    $ gzip -dc state-5.6.6.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.6.tgz

``state-5.6.6/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory

.. code:: bash

    $ cd state-5.6.6/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.intel_smith make.arch

and edit ``make.arch`` according to your environment. Then type

.. code:: bash

    $ make

You will get the executable ``STATE`` in the source directory.

For example, ``make.arch`` for the supercomputer (ohtaka) at ISSP, The University of Tokyo looks like::

    F90     = mpiifort
    LINKER  = mpiifort
    OMP     = -qopenmp
    OPT1    = -O1 -fp-model strict -axCORE-AVX2
    OPT3    = -O3 -fp-model strict -axCORE-AVX2
    FLAG    = $(OMP) $(OPT1) -zero -fixed -extend_source -xHOST
    FLAGS   = $(OMP) $(OPT3) -zero -fixed -extend_source -xHOST
    FLAGD   = $(OMP) $(OPT3) -zero -fixed -extend_source -xHOST
    FLAGNP  =        $(OPT3) -zero -fixed -extend_source -xHOST
    DEBUG   = 
    LIBS    = -mkl=parallel 
    LAPACK  =
    INCLUDE = -I$(MKLROOT)/include/fftw
    CPPDIR  = /usr/bin
    CPP     = $(CPPDIR)/cpp -P -C -traditional
    P_FLAGS = -D_INTEL_DAVIDSON_ -D_FFTW3_ -D_MKL_FFTW_ -D_TIMER_ -D_OPENMP_FUNC_ -D_TEST_

The ``make.arch`` for ohtaka with SCALAPACK looks like::

    F90     = mpiifort
    LINKER  = mpiifort
    OMP     = -qopenmp
    OPT1    = -O1 -fp-model strict -axCORE-AVX2
    OPT3    = -O3 -fp-model strict -axCORE-AVX2
    FLAG    = $(OMP) $(OPT1) -zero -fixed -extend_source -xHOST
    FLAGS   = $(OMP) $(OPT3) -zero -fixed -extend_source -xHOST
    FLAGD   = $(OMP) $(OPT3) -zero -fixed -extend_source -xHOST
    FLAGNP  =        $(OPT3) -zero -fixed -extend_source -xHOST
    DEBUG   = 
    LIBS    = -lmkl_scalapack_lp64 -lmkl_blacs_intelmpi_lp64 \
              -lmkl_intel_lp64 -lmkl_intel_thread -lmkl_core \
              -liomp5 -pthread -lm 
    INCLUDE = -I ${MKLROOT}/include/fftw
    CPPDIR  = /usr/bin
    CPP     = $(CPPDIR)/cpp -P -traditional
    P_FLAGS = -D_INTEL_DAVIDSON_ -D_FFTW3_ -D_MKL_FFTW_ -D_TIMER_ -D_OPENMP_FUNC_ -D_SCALAPACK_

To compile the utilities, go to the ``util`` directory, edit ``make.inc``, and type :

.. code:: bash

    $ make

Symbolic links to the utilities are created in the ``bin`` directory.

Use `Intel Math Kernel Library Link Line Advisor <https://software.intel.com/content/www/us/en/develop/articles/intel-mkl-link-line-advisor.html>`_ to find recommended libries for Intel fortran.

.. _platform:

Platform specific information
=============================

smith @ Morikawa group 
----------------------

sb100 @ Morikawa group 
----------------------

ohtaka @ ISSP
-------------

