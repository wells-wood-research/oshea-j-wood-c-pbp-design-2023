Welcome to our periplasmic binding protein biosensor design repo. Here is a description of what can be found in each directory.

## Simulations
#### Holo parameterisation
To run the holo simulations, first a PDB file was made for maltose (mal.pdb), from which mol2 and frcmod files were generated using Amber:

antechamber -fi pdb -i MAL.pdb -fo mol2 -o mal.mol2 -c bcc -at amber
parmchk2 -i mal.mol2 -f mol2 -o mal.frcmod

mal.lib was generated in tleap (tleap_mal.in). The topology for the holo complex could then be generated from the 1anf crystal structure, which has been modified to decribe the maltose as a sinle residue (crystal_bou.pdb, tleap_hol.in).


#### Apo parameterisation
An apo structure was generated by removing the maltose from 1anf (crystal_apo.pdb). This structure was parameterised in tleap (tleap_apo.in)

#### Running simulations
Simulations were run using OpenMM from the respective scripts 10x200ns_apo.py and 10x100ns_hol.py. These generated .dcd output files, which are not contained in the repository.


## CONAN
To generate input for CONAN, the molecular dynamics .dcd output files were converted to .xtc using the MDTraj function "mdconvert". The .xtc files are not included in the repository.
With CONAN installed, conan.py was on the CONAN input files (CONAN/conan1_X/conan1_x.inp). The only CONAN output directory stored in the repository is "aggregate", which contains the data to generate the Pearson Correlation Coefficient plots.


## Plotting Pearson Correlation Coefficient, dDIHE, dRMSF
Code to plot these data is contained in oshea-j-wood-c-pbp-design-2023.ipynb. For calculating dDIHE and dRMSF of the molecular dynamics simulations, it is assumed that the .dcd files are contained in "Simulations/Apo" and "Simulations/Holo", but, as previously stated, these files are not included in this repository.
