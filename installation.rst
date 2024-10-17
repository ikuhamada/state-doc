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

Change the directory to ``STATE/src`` and copy the source code ``state-5.6.15.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.15.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.15.tgz

``state-5.6.15/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.15/src


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

Change the directory to ``STATE/src`` and copy the source code ``state-5.6.15.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.15.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.15.tgz

``state-5.6.15/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.15/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.intel_sb100 make.arch

and edit ``make.arch`` according to your need. Then type

.. code:: bash

    $ make

You will get the executable ``STATE`` in the source directory.


ohtaka @ ISSP
-------------

On ohtaka at ISSP, we have confirmed that the following modules can be used safely (see a note below):

.. code:: bash

 1) oneapi_compiler/2023.0.0   2) oneapi_mkl/2023.0.0   3) openapi_mpi/2023.0.0


Change the directory to ``STATE/src`` and copy the source code ``state-5.6.15.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.15.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.15.tgz

``state-5.6.15/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.15/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.intel_ohtaka_scalapack make.arch

and type

.. code:: bash

    $ make

.. warning::
	When running a code build with Intel MPI (``oneapi_mpi/2023.0.0``), set ``export FI_PROVIDER=psm3`` in the job script, along with the modules used above.


kugui @ ISSP
-------------

On kugui at ISSP, we have confirmed that the following modules can be used safely (see a note below):

.. code:: bash

	Currently Loaded Modulefiles:
	  1) craype-x86-milan            4) perftools-base/23.03.0      7) cray-mpich/8.1.30          10) nvhpc-nompi/24.7_cuda12.5
	  2) libfabric/1.13.1            5) cce/18.0.0                  8) cray-libsci/23.02.1.1      11) openmpi_nvhpc/4.1.2
	  3) craype-network-ofi          6) craype/2.7.20               9) PrgEnv-cray/8.3.3          12) intel/2022.2.1

Change the directory to ``STATE/src`` and copy the source code ``state-5.6.15.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.15.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.15.tgz

``state-5.6.15/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.15/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.amd_kugui make.arch

and type

.. code:: bash

    $ make


SQUID @ Cybermedia Center, Osaka University
-------------------------------------------

On SQUID at Cybermedia Center, Osaka University, we use the following modules:

- BaseCPU
- BasePy

Current default modules are ``BaseCPU/2023`` and ``BasePy/2023``. Type or write the following to use these modules

.. code:: bash

	module load BaseCPU/2023
	module load BasePy/2023

Loaded modules are followings:

.. code:: bash

	 1) inteloneAPI/2023.0   5) compiler/latest   9) dal/latest                13) mkl/latest       17) BaseCPU/2023(default)  
	 2) tbb/latest           6) mpi/latest       10) inspector/latest          14) vtune/latest     18) python3/3.6            
	 3) compiler-rt/latest   7) advisor/latest   11) intel_ipp_intel64/latest  15) debugger/latest  19) BasePy/2023(default)   
	 4) oclfpga/latest       8) clck/latest      12) itac/latest               16) dpl/latest       

Change the directory to ``STATE/src`` and copy the source code ``state-5.6.15.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.15.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.15.tgz

``state-5.6.15/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.15/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.intel_squid make.arch

Then, type

.. code:: bash

    $ make


Wisteria @ Information Technology Center, The University of Tokyo
-----------------------------------------------------------------

On Wisteria/BDEC-01 Supercomputer System (Odyssey), The University of Tokyo, we use Fujitsu Development Studio compilers and MPI library and the following modules:

- fj
- fjmpi
- mpi-fftw

Type or write the following to use these modules

.. code:: bash

	module load fj
	module load fjmpi
	module load mpi-fftw


Loaded modules are followings:

.. code:: bash

	Currently Loaded Modulefiles:
	 1) fjmpi/1.2.39   2) fj/1.2.39(default)   3) mpi-fftw/3.3.9  


Change the directory to ``STATE/src`` and copy the source code ``state-5.6.15.tgz`` from my directory, and unpack the source code there:

.. code:: bash

    $ gzip -dc state-5.6.15.tgz | tar xf -

or

.. code:: bash

    $ tar zxf state-5.6.15.tgz

``state-5.6.15/`` contains the following file and directories::

    README  arch/   build/  src/    util/

Go to the source directory:

.. code:: bash

    $ cd state-5.6.15/src


make a symbolic link to ``make.arch`` as follows, e.g.

.. code:: bash

    $ ln -s ../arch/make.arch.fx1000 make.arch

Then, type

.. code:: bash

    $ make

