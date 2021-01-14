## Vdw README

* 1) databaseparser identifies missing vdw parameters by checking if all neighbors of each atom are contained within the best match SMART string assigned. If not, then parameter is defined as missing, the program chooses one example in molecule corresponding to that parameter type.
* 2) water-molecule dimers are created with H and O oriented towards the atom with missing vdw parameters.
* 3) geometry optimization is performed on the dimer
* 4) 5 dimer structures are created by shifting the water probe about the QM minima obtained from geometry optimization
* 5) each structure undergoes SP QM to obtain reference target energies for the fitting procedure.
* 6) Initial guess parameters from databaseparser assignment and lower, upper bounds are defined with 10% +/- initial parameter guesses.
* 7) Fitting procedure continously calls analyze while modifying tinker key file.
* 8) final parameters and fitting results are plotted
