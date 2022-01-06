===========
About STATE
===========

STATE is a plane-wave pseudopotetial implementation of the electronic structure
calculations and ab initio molecular dynamics simulations based on density
functional theory within the local, semilocal, and nonlocal density functionals.

The code is written in Fortran90 and parallelized using MPI and OpenMP.

STATE can perform the following calculations:

* Electronic minization with the Davidson or RMM-DIIS method
* Real-space projection of the nonlocal pseudopotentials for an efficient calculation
* Various exchange-correlation functional: LDA, GGA, GGA+U, and vdW-DF 
* Structural optimization with quenched molecular dynamics (aka QuickMin), GDIIS, or FIRE (experimental)
* Reaction path search via the CINEB method
* Born-Oppenheimer molecular dynamics simulation with NVE or NVT ensemble
* Blue-moon ensemble or metadynamics for free energy sampling
* Effective screening medium method for a charged slab calculation
* Electronic structure analysis: band structure and density of states
* Vibrational mode analysis via the finite difference method

Developers
----------

- Yoshitada Morikawa (Osaka University)
- Koji Inagaki (Osaka University)
- Yuji Hamamoto (Osaka University)
- Ikutaro Hamada (Osaka University)

Contributers
------------

- Tamio Ikeshoji (AIST)
- Zhong Fang (CAS)
- Takashi Ikeda (JAEA)
- Minoru Otani (AIST)
- Osamu Sugino (University of Tokyo)
- Teruo Hirakawa (Osaka University)

How to cite STATE
-----------------

So far, there are no papers describing the STATE code.
However, to acknowledge the efforts devoted to make the code available to the community,
we suggest to cite the following paper(s)

- Y. Morikawa, H. Ishii, and K. Seki, Phys. Rev B **69**, 041403 (2004).
- Y. Morikawa, Phys. Rev. B **63**, 033405 (2001).
- Y. Morikawa, K. Iwata, and K. Terakura, Appl. Sur. Sci **169-170**, 11 (2001).

We appreciate if you cite the following paper, when you use the van der Waals functional:

- Y. Hamamoto, I. Hamada, K. Inagaki, and Y. Morikawa, Phys. Rev. B **93**, 245440 (2016).

This paper describes our implementation of the self-consistent vdW-DF of Wu and Gygi [J. Chem. Phys. **136**, 224107 (2012)].

Credit
------

Sasfan Arman Wella created the STATE logo.

