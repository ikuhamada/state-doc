============
Installation
============

.. warning::
	This page is under construction

Obtaining the code
==================

The code and pseudopotentials can be obtained upon request to the STATE developers.

Compilation
===========


  Unpack the source code::

    $ gzip -dc state-5.6.6.tgz | tar xf -

  or::

    $ tar zxf state-5.6.6.tgz

  state-5.6.6/ contains the following file and directories::

    README  arch/   build/  src/    util/

  Go to the source directory::

    $ cd state-5.6.6/src


  make a symbolic link to ``make.arch`` as follows, e.g.::

    $ ln -s ../arc/make.arch.intel_smith make.arch

  and edit ``make.arch`` according to your environment. Then type::

    $ make

  You will get the executable ``STATE`` in the source directory.


  For example, ``make.arch`` for the supercomputer (ICE XA) at ISSP, The University of Tokyo looks like::

    F90    = mpiifort
    LINKER = mpiifort
    OMP    = -qopenmp
    OPT1   = -O1 -fp-model strict -axCORE-AVX2
    OPT3   = -O3 -fp-model strict -axCORE-AVX2
    FLAG   = $(OMP) $(OPT1) -zero -fixed -extend_source -xHOST
    FLAGS  = $(OMP) $(OPT3) -zero -fixed -extend_source -xHOST
    FLAGD  = $(OMP) $(OPT3) -zero -fixed -extend_source -xHOST
    FLAGNP =        $(OPT3) -zero -fixed -extend_source -xHOST
    DEBUG  = 
    LIBS   = -mkl=parallel -lmkl_scalapack_lp64 -lmkl_blacs_intelmpi_lp64 -lmpi
    LAPACK =
    INCLUDE = -I$(MKLROOT)/include/fftw
    CPPDIR  = /usr/bin
    CPP     = $(CPPDIR)/cpp -P -C -traditional
    P_FLAGS  = -D_FFTW3_ -D_MKL_FFTW_ -D_TIMER_ -D_SCALAPACK_ -D_OPENMP_FUNC_ -D_TEST_
  

  To compile the utilities, go to the ``util`` directory, edit ``make.inc``, and type ::

    $ make

  Symbolic links to the utilities are created in the ``bin`` directory.

  Use `Intel Math Kernel Library Link Line Advisor <https://software.intel.com/content/www/us/en/develop/articles/intel-mkl-link-line-advisor.html>`_ to find recommended libries for Intel fortran.
