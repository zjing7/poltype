## Databaseparser README
* Bond and Angle equilibrium values are taken from QM opt structure
* amoeba09.prm molecule parameters are assigned SMART strings to their corresponding tinker type numbers
* databaseparser will fragment the input molecule and attempt to match molecule SMART strings to SMARTS associated with amoeba09. The largest environment (largest SMARTS) match from amoeba09 to input molecule is determined with this protocol.
* If a match of length=number of input atoms (1 for van der waals, 2 for bond, 3 for angle, 4 for torsion) is not found, then first wild card bonds are used (try to match to any bond type).
* If wild card bonds do not find a match, then one of the atoms on the end is converted to a wild type atom (tries to match any atom)
* If that does not work, then next the other end of the string is converted to a wild card atom
* If that does not find a match, then both ends are converted to a wild card atom
* If that does not find a match, then all atoms are converted into wild card atom


* external database smarts for bond,angle, torsion, vdw can be added and then size of match is compared to best match from amoeba09 to determine which parameters to use
## Torsion
* Missing torsion parameters are defined as if bond is not acid, not amide, not double or aromatic and if the best smarts match does not contain all atoms in torsion a-b-c-d + all neighboring atoms in the smarts string environment.
* If a or d in a-b-c-d is a hydrogen and not all a and d around b-c is hydrogen, then this torsion is only transferred and not defined as missing

## Van der Waals
* Missing van der waals parameters are defined when best smarts match does not contain atom index + all neighbors of atom index in the smarts string envioronment


## Opbend
* Default opbend parameters from mm3 are used when opbend parameters are not found from amoeaba09
