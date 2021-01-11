* [ ] For bond, angle in SMARTS match, if atoms+all neighbors are not in SMARTS (hybridization is not implicit) then default to MM3 bond/angle parameters
* [ ] Add van der waals automated fitting to poltype
* [ ] If SMARTS match does not include atom+all neighbors for vdw, then go to automated fitting, make a fragment and transfer vdw parameters from fragment
* [ ] Fix tor-tor bugs (if one bond missing torsion but adjacent is not, then spin both and force tor-tor) , also transfer tor-tor to database allow databaseparser to read and transfer tor-tor
* [ ] Turn tor-tor and ringtor on by default
* [ ] Update examples in examples folder, fix unittesting module that used parmed
* [ ] Big documentation update
* [ ] Modifiedresidue library fix/ bugs update features (edited)
* [ ] Add error.log, print errors to both error.log and poltype.log
* [ ] Add top folder with final key/xyz
* [ ] If key_5 final has an error, rename it to key_5.error (missing torsion)
* [ ] Add README_TROUBLESHOOTING page (copy content from README_HELP). 
* [ ] Docker contained for Linux OS
* [ ] Give input option to add hydrogen.
* [ ] Add more sophisticated zwitterion detection.
* [ ] Add comments to every function in poltype with the fields below
    Intent: 
    Input:
    Output: 
    Referenced By: 
    Description
* [ ] Determine molecules to test
