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

Having obtained the source code, say ``state-5.6.10.tgz``, unpack the source code under ``src`` as

.. code:: bash

    $ gzip -dc state-5.6.10.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.10.tgz

``state-5.6.10/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory

.. code:: bash

    $ cd state-5.6.10/src


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

First, make sure modules are loaded as appropriate. Type:

.. code:: bash

    $ module avail

and you can see as follows::

      1) intel/2020.2.254      2) intelmpi/2020.2.254   

If not, type the following:

.. code:: bash

    $ module load intel/2020.2.254
    $ module load intelmpi/2020.2.254

Change the directory to ``STATE/src`` and copy the source code ``state-5.6.10.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.10.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.10.tgz

``state-5.6.10/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.10/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.intel_smith make.arch

and edit ``make.arch`` according to your need. Then type

.. code:: bash

    $ make

You will get the executable ``STATE`` in the source directory.


sb100 @ Morikawa group 
----------------------

As in the case of smith, make sure modules are loaded as appropriate. Type:

.. code:: bash

    $ module avail

and you can see as follows::

     1) intel/2021.2.0   2) intelmpi/2021.2.0  

If not, type the following:

.. code:: bash

    $ module load intel/2021.2.0
    $ module load intelmpi/2021.2.0

Change the directory to ``STATE/src`` and copy the source code ``state-5.6.10.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.10.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.10.tgz

``state-5.6.10/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.10/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.intel_sb100 make.arch

and edit ``make.arch`` according to your need. Then type

.. code:: bash

    $ make

You will get the executable ``STATE`` in the source directory.


ohtaka @ ISSP
-------------

On ohtaka at ISSP, we have confirmed that the following modules can be used safely (as of April 24, 2023):

.. code:: bash

 1) oneapi_compiler/2023.0.0   2) oneapi_mkl/2023.0.0   3) openmpi/4.1.5-oneapi-2023.0.0-classic  


Change the directory to ``STATE/src`` and copy the source code ``state-5.6.10.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.10.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.10.tgz

``state-5.6.10/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.10/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.intel_ohtaka_scalapack make.arch

and edit ``make.arch`` according to your need. We typically need the following changes in ``make.arch``::


  F90    = mpif90
  LINKER = mpif90
  OMP    = -qopenmp

and

.. code:: bash

  LIBS   = -lmkl_scalapack_lp64 -lmkl_blacs_openmpi_lp64 \
           -lmkl_intel_lp64 -lmkl_intel_thread -lmkl_core

After the edit, type

.. code:: bash

    $ make


