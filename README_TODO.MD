* [ ] If hydrogen torsion is removed from fitting because paramters are too close to zero, report in poltype log, then in fragmenter report to whole molecule log
* [ ] If fragment is same as parent, skip fragmenter and just do normal poltype
* [ ] Change ttt.xyz and ttt.key to final.xyz and final.key
* [ ] Add error.log, print errors to both error.log and poltype.log
* [ ] Add top folder with final key/xyz
* [ ] If key_5 final has an error, rename it to key_5.error (missing torsion)
* [ ] Add RaiseValue error for when child poltype job has not completed (doesnt have key_5), otherwise people use fragmenter and wont read the parent poltype log that contains all of the errors from any child jobs
* [ ] For some reason old poltype did not restrain hydrogen torsion on QM (even though MM does) , make sure it is apples to apples
* [ ] Add README_TROUBLESHOOTING page (copy content from README_HELP). 
* [ ] Docker contained for Linux OS
* [ ] Give input option to add hydrogen.
* [ ] Make sure of key_3 already exist, dont redo fitting of esp.
* [ ] Fix bug where WithIndex and WithoutIndex.png have no index. Make sure all molecules in image either have indexes or dont. 
* [ ] Raise ValueError if final key file has any torsion zeroed out (possible that database had no matches)
* [ ] For any hydrogen torsion assign prior SMART string and parameters to reduce the amount of parameters needed to fit for rotatable bonds
* [ ] Add map from Tinker Type Number to SMART string chemical enviornment
* [ ] Using the above map, autogenerate torsion, vdw ... parameters from .prm file inside poltype. Keep user added parameters in seperate dictionaries. 
* [ ] For a given node, RAM, processor number and disk usage, can we parralelize QM jobs for a single node (as opposed to just submitting one job per node?)
* [ ] For any autofitting and fragment SMARTS generation,also include metrics for RMSED for fitting in comments (can be automated) so future users know how bad fit is 
* [ ] Fix bugs in modifedresidue.py, also fix bug giving excess charge (small) when starting with neutral input molecule.
* [ ] add z-x-y multipole frame for chiral atoms
* [ ] Test fragmenter on drugbank database (dont paramterize until the rest of POLTYPE torsion is complete)
* [ ] Allow ring torsions to be puckered and obtain QM data for torsion paramterization
* [ ] Allow 2D dihedral scans to fit a tor-tor coupling term too for torsions that are adjacent to each other. Numerical spline should be used for functional form of tor-tor.
* [ ] Add automated vdw QM surface scan from water probes. Add this BEFORE torsion fitting, so that you always do torsion last. If user decides to do vdw fitting after key_5 already generated need to remove the key5 then and refit torsion.
* [ ] Add comments to every function in poltype with the fields below
    Intent: 
    Input:
    Output: 
    Referenced By: 
    Description 
