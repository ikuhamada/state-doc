===========
About STATE
===========

STATE is a plane-wave pseudopotetial implementation of the electronic structure
calculations and ab initio molecular dynamics simulations based on density
functional theory within the local, semilocal and nonlocal density functional.

The code is written in Fortran90 and parallelized using MPI and OpenMP.

STATE can perform the following calculations:

* Electronic minization with Davidson or RMM-DIIS method
* Electronic structure analysis: band structure and density of states
* Structural optimization with quenched molecular dynamics (aka QuickMin) or GDIIS
* Reaction path search via the CINEB method
* Born-Oppenheimer molecular dynamics simulation with NVE or NVT ensemble
* Blue-moon ensemble or metadynamics for free energy sampling
* Real-space projection of the nonlocal pseudopotentials for an efficient calculation
* Effective screening medium method
* Various exchange-correlation functional: LDA, GGA, GGA+U, and vdW-DF 

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

