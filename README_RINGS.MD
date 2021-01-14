## Rings README

* N-dimensional torsion scans are required for ring puckering and torsion parameter refinement.
* The number of dimensions is R-3, where R is the number of bonds on non-aromatic ring.
* Rotatable bonds are chosen as close as possible to each other (consecutively) to prevent torsion restraints from     fighting with each other.
* A grid of length (50 degrees)^N with 10 degree intervals.
* the fragmenter module will create a fragment for every non-aromatic ring and then transfer parameters after torsion fitting is completed, back to the parent molecules key file.
* poltype has a default number of 40 grid points to run QM computations for any single fragment. So even if there are more possible points on the defined grid, poltype uniformaly keeps only 40 by default. 
