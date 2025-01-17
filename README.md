# Organic redox potentials from quantum chemsitry/ML with GPs

![Graphical abstract](toc.png)

A mixed quantum chemistry/machine learning approach for the fast and accurate prediction of biochemical redox potentials and its large-scale application to 315,000 redox reactions

Preprint link: <https://doi.org/10.1101/245357>

This repo contains:

* Data for the article (**data** folder).
* Code to calibrate a gp on experimental data and create fingerprint analysis. (**GP_calibration.ipynb)**
* Reaction expansion network code (**redox_net_code**).

## Data

All data is containted in the data folder, the description of each file is:

* **KEGG_compounds.csv** contains information on the 12k natural metabolites from the KEGG database, used as seed compounds in the redox network expansion algorithm.
* **redox_mols.csv** contains the 76k compounds generated by the redox network expansion algorithm. In particular we introduce a label e.g. 'Z0052' to later reference for calculations. Also includes protonation state information such as pKAs, SMILES@ph7, major micro species at pH7 and charges.
*  **redox_pm7.csv** contains electronic energies in HA for all 76k molecules, with and without solvation.
* **model_chemistries** is a folder with 14 csv files, each containing information of calculated electronic energies for our model selection and GP-training. In most cases, the model chemistry consists of a pair of theory for energy and geometry, e.g 'HF3c_uff.csv' is HF3-c calculations on a UFF-optimized geometry. Additionally statistics can be found when available. Some model chemistry contain around ~750 entries while others ~150, based on their potential for being a good model.
* **redox_experimental.csv** contains experimental standard redox potentials for a set of 125 biochemical reactions compiled from the [NIST database](https://randr.nist.gov/enzyme/). For sake of completeness it also contains other reaction categories (1 & 4).
* **redox_calibration.csv** containts experimental and calculated data (~80 datapoint) for the GP calibration.
* **redox_results.csv** contains predictions for 315k redox reactions. We have the standard redox potential (ORP) using PM7 and calibrated with linear and GP regression.

Looking for more data? Send us an email, we tried to keep the data as most concise as possible but we have several GBs of calculation files (PM7 and quantum chemistry).

## Sotfware

* python 3
* rdkit (tested on 2017.03.03)
* numpy, scipy, seaborn, pandas
* gpmol (tensorflow, gpflow)

It should be noted that rdkit 2018.09.01 has changes to the rxn code relating to chiralality in smiles, which increases the number of resulting compounds of the rxn generation code.

## Todo

- [ ] Upload environment.yml
- [ ] Polish ipython notebook
- [ ] Upload GP mol.
