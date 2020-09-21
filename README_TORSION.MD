## Torsion README

* Below is a high level flow of how torsion scanning works

* 2D torsion scanning is not yet supported.

* If doing a rigid rotation scan (all torsions around bond move together), all torsions around other bonds are restrained during optimization

* If doing a vibrational torsion scan, (slightly move one torsion around bond without moving others), all torsions around other bonds are restrained during optimization as well as all torsion besides the one being moved around rotatable bond

* Vibrational torsion scans will help partition the total QM-MM energy around a rotatable bond into UNIQUE parameter solutions for each individual torsion, giving a more accurate vibrational potential energy surface. This feature is not yet implmented in Poltype.

* Currently you still need to check for missing torsion parameters in final key file (could be due to quantum jobs failing/not submitted correctly, or poltype decides the torsion contribution is neglible during fitting (for example some hydrogen torsions contribute small energy to total torsions around rotatable bonds). 

* If you see the below line above a torsion keyword in the keyfile, this means the torsion was transferred from the database. The SMARTS string assignment is provided along with the corresponding atom indidces. The smiles torsion indices refer to the positions of the torsion indices within the SMARTS fragment, some SMARTS strings have more than ffour atoms and thus it is possible that the four torsion atoms in the SMARTS string is not the first four (1,2,3,4). 
* [c][c] is an example of an aromatic ring bond, [C][C] is an example of an aliphatic single bond. Single bonds can be denoted with - as well (or if no bond character, single is assumed). Double bonds are denoted with = (: for aromatic  bonds).

```
# Transferred Torsion assigned from SMARTS [#1][C][C][#1] torsion atom indexes = 8,7,5,6 with smiles torsion indices 1,2,3,4
```

* If you see the below line this means the torsion line below this line was fitted and transferred from a fragment. The information provided above in the case of database transfer is the same.
```
# Fitted and Transferred from Fragment  SMARTS [#6](\[H])(-[#6]-[H])=[#6](\[#6]-[H])-[H] torsion atom indexes = 1,4,5,8 with smiles torsion indices 1,5,6,7
```
* The below line is the database format for the parameters + SMART string (for putting into database after deriving) parameters
```
# "[#6](\[H])(-[#6]-[H])=[#6](\[#6]-[H])-[H]" : [8,5,6,7,0.096,-0.060,0.097], \\

```

* By default the number of missing torsions x the number of cosine terms (default is three) determine how many quantum points to sample along the dihedral surface , if the number is greater than 12, else 12 is the default. 

* Equal weights are used for torsion fitting along QM-MM1 energy surface, where MM1 is initial guess torsion parameters. If the RMSD(QM,MM2) fails to pass a threshold tolerance, than fitting is redone where the target QM-MM1 is modified with boltsman like weights based on the QM energy surface to favor minima.

![Torsion Protocol](Images/TorsionProtocol.PNG)

* Below is more detailed flow of how files are generated

![Torsion Protocol](Images/TorsionProtocolDetailed.PNG)

* Below is a high level flow of how torsion fitting works

![Torsion Fitting Protocol](Images/TorsionFittingProtocol.PNG)

* Below is a plot of QM-MM and the coresponding fit vs dihedral angle

* At the top of the plot, all torsions (in type number format) are shown being fit around rotatable bond

![QM-MM](Images/QM-MM.png)

* Below is a plot of total QM, MM energies vs dihedral angle

* At the top is the Absolute RMSD between MM2 and QM (Abs=) and a weigted RMSD between MM2 and QM (Wei), where the weight is the form of a boltzman function where w*(QM-MM) and w=1/e^)((QM-MM)/2.5)

* If the RMSD=0 there is a perfect fit between MM2 (post fitting parameters) and QM energy curves

![Tor Energy](Images/TorEnergy.png)


