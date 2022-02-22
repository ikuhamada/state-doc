.. _appendix:

========
Appendix
========

.. warning::
        This page is under construction

History of STATE
----------------

The development of the original plan-wave pseudopotential code dates back to the middle of 1980's, and STATE has been developed continuously in collaboration with many colleagues mainly in Japan, in the Joint Research Center for Atom Technology (JRCAT) of the National Institute for Advanced Interdisciplinary Research (NAIR), then in Institute of Scientific and Industorial Research, Osaka University, and in Graduate School of Engineering, Department of Precision Eigineering, Osaka University.

The history of the developement of the STATE code is be briefly (not really;-)) summarized as follows: H. Ishida developed a norm-conserving pseudopotential and plane-wave code from scratch at the Institute for Solid State Physics, University of Tokyo. K. Kobayashi introduced modified the steepest descent algorithm and Kleinman-Bylander type separable pseudopotential scheme. Y. Morikawa introduced the ultrasoft pseudopotentials. T. Yamasaki, K. Kato, and Y. Morikawa parallelized the code for Fujitsu VPP and introduced the generalized gradient approximation and spin polarization. T. Miyazaki introduced the linear tetrahedron method. Y. Morikawa introduced LDA+U, Davidson, Blugel charge densit mixing scheme, generalized direct inversion of iterative subspace (GDIIS) for the geometry optimization, and the Perdew-Burke-Ernzerhof exchange-correlation functional. Z. Fang rewrote the code in fortran90 and parallelized it with the message passing interface. T. Sanada, Z. Fang, and Y. Morikawa implemented the residual verctor minimization method (RMM) and real space projectors. T. Ikeda and T. Uchiyama introduced the Nose-Hoover thermostat and blue moon ensemble method. I. Hamada and M. Otani implemented the effective screening medium (ESM) method. K. Lee implemented a post-processing code for the non-self-consistent van der Waals density functional (vdW-DF). The real-space non-selfconsistent vdW-DF was implemented based on the post-processing code by K. Lee. Grimme's DFT-D2 scheme was implemented by I. Hamada. K. Inagaki implemented the blocked orthonormalization scheme and replica parallelization scheme for the nudged elastic band and blue-moon ensemble calculations. K. Inagaki and M. Haraguchi introduced replica + k-point + band + G-point + thread five-fold parallelization. S. Yanagisawa implemented an interace to the space-time GW code. I. Hamada implemented the Hellmann-Feynman force in DFT+U with the ultrasoft pseudopoteital. T. Hirakawa and K. Inagaki implemented the metadynamics method for multi-dimensional free-energy surface calculations. I. Hamada and Y. Hamamoto introduced the efficient self-consistent implementation of vdW-DF of Wu-Gygi. I. Hamada enabled the fixed moment calculation based on the work by J. I. Enriquez. Hamada introduced spin vdW-DF. I. Hamada introduced a free-format input style.


