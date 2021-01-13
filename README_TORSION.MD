## Torsion README


![Torsion Protocol](Images/TorsionProtocol.PNG)

* Below is more detailed flow of how files are generated

![Torsion Protocol](Images/TorsionProtocolDetailed.PNG)



### Torsion Database Parameter Assignment
* databaseparser.py will first try to match fragments of input molecule to amoeba09 small molecule database to assign parameters.
* If any wild cards are detected (~, *) or the torsion (a-b-c-d) does not include all neighbors of (a-b-c-d) in the best matched SMART string, then torsion parameterization will be done by torsiongenerator, fragmenter and torsionfit libaries.
* Double bonds and aromatic ring bond torsion parmeters are always transfered from best match.
* If hydrogen exists for either a or d in a-b-c-d and not all possible a and d are hydrogen for all torsion around b-c, then the torsion a-b-c-d containing hydrogen is only transferred from database and does not proceed tor torsion paramterization by torsiongenerator, fragmenter and torsionfit.


### Torsion Grid Setup

* If the variable tortor is turned on, then torsion-torsion 2D dimensional scans are done for neighboring rotatable    bonds that are missing parameters. If either torsion on one of the rotatable bonds is missing, then 2D torsion grid  scan will be used to obtain tor-tor and also 1D torsion parameters.
* poltype has a default number of 40 grid points to run QM computations for any single fragment. So even if there are more possible points on the defined grid, poltype uniformaly keeps only 40 by default. 

* By default the number of missing torsions x the number of cosine terms (default is three) determine how many quantum points to sample along the dihedral surface , if the number is greater than 12, else 12 is the default. 


### Torsion Fiting

* Equal weights are used for torsion fitting along QM-MM1 energy surface, where MM1 is initial guess torsion parameters. If the RMSD(QM,MM2) fails to pass a threshold tolerance with absolute and relative RMSD, then fitting is redone where the target QM-MM1 is modified with boltzsman like weights based on the QM energy surface to favor minima.


* Below is a high level flow of how torsion fitting works

![Torsion Fitting Protocol](Images/TorsionFittingProtocol.PNG)

* Below is a plot of QM-MM and the coresponding fit vs dihedral angle

* At the top of the plot, all torsions (in type number format) are shown being fit around rotatable bond

![QM-MM](Images/QM-MM.png)

* Below is a plot of total QM, MM energies vs dihedral angle

* At the top is the Absolute RMSD between MM2 and QM (Abs=) and a weigted RMSD between MM2 and QM (Wei), where the weight is the form of a boltzman function where w*(QM-MM) and w=1/e^)((QM-MM)/2.5)

* If the RMSD=0 there is a perfect fit between MM2 (post fitting parameters) and QM energy curves

![Tor Energy](Images/TorEnergy.png)

* If you see the below line above a torsion keyword in the keyfile, this means the torsion was transferred from the database. The SMARTS string assignment is provided along with the corresponding atom indidces (if atom indices are the same, this just means that the actual atom indices share same type numbers). The smiles torsion indices refer to the positions of the torsion indices within the SMARTS fragment, some SMARTS strings have more than four atoms and thus it is possible that the four torsion atoms in the SMARTS string is not the first four (1,2,3,4). 
* [c][c] is an example of an aromatic ring bond, [C][C] is an example of an aliphatic single bond. Single bonds can be denoted with - as well (or if no bond character, single is assumed). Double bonds are denoted with = (: for aromatic  bonds).
```
# matching SMARTS from molecule  ['[#6]~[#6]~[#6](~[#8])~[#6]', [1, 5, 3, 4]] to SMARTS from parameter file ['[#8](-[#6]1:[#6](:[#6](:[#6](:[#6](:[#6]:1-[H])-[H])-[H])-[H])-[H])-[H]', [6, 7, 2, 1]] with tinker type descriptions [('C', '"Phenol C3"'), ('C', '"Phenol C2"'), ('C', '"Phenol C1-OH"'), ('O', '"Phenol OH"')]
```


