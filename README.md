# IF-SitePred

IF-SitePred is a method for predicting ligand-binding sites on protein structures. It first generates an embedding for each residue of the protein using the [ESM-IF1 (inverse folding)](https://github.com/facebookresearch/esm/tree/main/examples/inverse_folding) model, then performs point cloud clustering to identify binding site centres. 

## Installation

Follow the following steps to prepare two virtual environments for IF-SitePred:

#### A) Clone repository
```
git clone https://github.com/annacarbery/binding-sites
```

#### B) Create environment containining ESM

1. Create and activate virtual environment
```
conda create -n esm_env
conda activate esm_env
```
2. Install esm
```
pip install fair-esm
```
3. Install [torch](https://pytorch.org/) (system-dependent, see instructions in torch documentation)
4. Install remaining dependencies
```
pip install scipy
pip install torch-geometric
pip install torch-scatter
pip install biotite
pip install lightgbm
pip install scikit-learn
```

#### C) Create environment containing PyMOL

1. Create and activate virutal environment with pymol installed
```
conda create -n pymol_env -c conda-forge -c schrodinger pymol-bundle -y
conda install -c conda-forge scikit-learn
conda activate pymol_env
 ```

## Command line use

1. Place PDB file of target of interest in 'input' directory
2. Activate environment with ESM installed
```conda activate esm_env```
3. Run residue prediction script:
```python src/predict_residues.py -t <target_name>```
4. The residues predicted to be binding are saved in the 'predictions' directory
5. Activate environment with PyMOL installed
```conda activate pymol_env```
6. Run centre prediction script:
```python src/predict_centres.py -t <target_name>```
7. The three top-ranked sites and their centres will be saved in the 'predictions' directory

## Issues

Please report issues at https://github.com/oxpig/binding-sites 

## Citation

Carbery, A., Buttenschoen, M., Skyner, R. et al. Learnt representations of proteins can be used for accurate prediction of small molecule binding sites on experimentally determined and predicted protein structures. J Cheminform 16, 32 (2024). https://doi.org/10.1186/s13321-024-00821-4 

