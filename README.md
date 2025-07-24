# Chemistry Projects

A collection of cheminformatics and computational chemistry workflows showcasing deep learning, machine learning, and Spark–based pipelines.

---

## Projects Overview

1. 🧪 **Quantum Chemistry Energy Prediction with GNNs** (`ANI-1`)
2. 🔬 **BTK Inhibitor Potency Prediction** (`BindingDB`)
3. 📈 **Zinc10M QSAR Pipeline** (`Zinc10M`)

---

## 1. Quantum Chemistry Energy Prediction with GNNs

**Notebook:** `ANI-1/ANI-1 shards.ipynb`

Predict quantum chemical conformer energies from the ANI-1 dataset using a SchNet Graph Neural Network (GNN), achieving **chemical accuracy** (MAE < 1 kcal/mol).

**Key Features:**

* On-the-fly HDF5 data loader for sharded ANI-1 shards
* Baseline energy correction via atomic contributions
* SchNet architecture implemented with PyTorch Geometric
* Saliency‐map interpretation of learned potentials

**Results:** MAE = 0.51 kcal/mol on held-out test set

**Technologies & Libraries:**

```
Python 3.11+
PyTorch >=2.0
PyTorch Geometric >=2.4
h5py >=3.9
pandas >=2.0
numpy >=1.24
matplotlib, seaborn, tqdm
```

---

## 2. BTK Inhibitor Potency Prediction

**Notebook:** `BindingDB/BindingDB.ipynb`

End-to-end ML workflow to predict pIC₅₀ bioactivity against Bruton's Tyrosine Kinase (BTK) from BindingDB.

**Workflow Steps:**

1. Data ingestion & filtering with PySpark
2. Descriptor calculation via RDKit (physicochemical + Morgan fingerprints)
3. RandomForestRegressor training & randomized hyperparameter search
4. Model evaluation (RMSE, R²) and residual analysis
5. 3D structure visualization of top hits using py3Dmol

**Core Packages:**

```
pyspark, pandas, numpy, rdkit-pypi
scikit-learn, matplotlib, seaborn, py3Dmol, tqdm
```

---

## 3. Zinc10M QSAR Pipeline

**Notebook:** `Zinc10M/Zinc10MQSAR.ipynb`

A scalable QSAR pipeline predicting lipophilicity (log P) for 10 million ZINC15 compounds.

**Pipeline:**

* Data ingestion via PySpark + sampling to pandas
* SMILES → RDKit molecules
* Calculation of 2D descriptors & ECFP4 fingerprints
* Train/test split + 5‑fold cross‑validation
* Random Forest regression modeling
* Performance analysis (RMSE ≈ 0.60, R² ≈ 0.80)
* Feature‐importance & descriptor–log P correlation plots

**Dependencies:**

```
pyspark, pandas, rdkit-pypi, scikit-learn
matplotlib, seaborn, tqdm
```

---

## Setup & Installation

1. **Clone this repository**

```bash
git clone https://github.com/Makayacine/Chemistry.git
cd Chemistry
```

2. **Create & activate environment**

```bash
# venv
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

# or Conda
conda create -n chem-env python=3.11
conda activate chem-env
```

3. **Install common dependencies**

```bash
pip install -r requirements.txt
```

4. **Project-specific data placement**

* **ANI-1:** HDF5 shards → `ANI-1/data/`
* **BindingDB:** `BindingDB_All.tsv` → `BindingDB/data/`
* **Zinc10M:** `zinc15_10M_2D.csv` → `Zinc10M/data/`

---

## How to Run

Launch JupyterLab or Notebook:

```bash
jupyter lab   # or jupyter notebook
```

Open and execute each project’s notebook in serial:

* `ANI-1 shards.ipynb`
* `BindingDB.ipynb`
* `Zinc10MQSAR.ipynb`

---

## Contributing

Contributions, issues, and feature requests are welcome!
Please open an issue or submit a pull request with a clear description of your changes.

---

*© 2025 Vince*
