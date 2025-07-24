# 🧪 Quantum Chemistry Energy Prediction with GNNs

This project demonstrates how to train a **SchNet** Graph Neural Network (GNN) to predict the quantum chemical energies of molecular conformers from the **ANI-1 dataset**. The model achieves **chemical accuracy** (Mean Absolute Error \< 1 kcal/mol) on the test set.

-----

## 📊 Project Overview

The goal of this study is to build a deep learning model that can accurately predict the energy of a molecule given the 3D coordinates of its atoms. This has significant applications in computational chemistry, materials science, and drug discovery, as it can replace or accelerate expensive simulations like Density Functional Theory (DFT).

The notebook (`ANI-1 shards.ipynb`) provides a complete workflow, including:

  - An efficient on-the-fly data loader for the large, sharded HDF5 dataset.
  - Preprocessing by calculating atomic baseline energies and training on **residual energies**.
  - Training and evaluation of a **SchNet** model using PyTorch Geometric.
  - Analysis of the results and model interpretation using saliency maps.

### Key Results

The final model achieves a **Mean Absolute Error (MAE) of 0.51 kcal/mol** on the unseen test set, successfully meeting the chemical accuracy benchmark.

-----

## 🚀 Technologies & Libraries

This project is built using the following core libraries:

  - **Python 3.11+**
  - **PyTorch**
  - **PyTorch Geometric** (for GNNs)
  - **scikit-learn** (for baseline energy fitting)
  - **pandas** (for results analysis)
  - **h5py** (for reading the dataset)
  - **Matplotlib & Seaborn** (for plotting)
  - **tqdm** (for progress bars)

-----

## ⚙️ Setup and Installation

To run this project, it's recommended to use a virtual environment.

**1. Clone the repository:**

```bash
git clone https://github.com/Makayacine/Chemistry.git
cd Chemistry
```

**2. Create and activate a virtual environment:**

```bash
# Using venv
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Or using Conda
conda create -n qm-gnn python=3.11
conda activate qm-gnn
```

**3. Install the required packages:**
A `requirements.txt` file is provided. Install it using pip:

```bash
pip install -r requirements.txt
```

**4. Download the Data:**
This project uses the ANI-1 dataset. Download the HDF5 shards and place them in a directory. Update the `data_path` variable in the notebook's configuration cell to point to your data files (e.g., `"path/to/your/data/ani_gdb_s0?.h5"`).

-----

## ▶️ How to Run

1.  Ensure your environment is activated and all packages are installed.
2.  Make sure the dataset is downloaded and the path in the notebook is correct.
3.  Launch Jupyter Notebook or JupyterLab:
    ```bash
    jupyter notebook
    ```
4.  Open and run the cells in `ANI-1 shards.ipynb`.

-----

## `requirements.txt`

```text
torch>=2.0.0
torch_geometric>=2.4.0
numpy>=1.24.0
pandas>=2.0.0
scikit-learn>=1.3.0
h5py>=3.9.0
matplotlib>=3.7.0
seaborn>=0.12.0
tqdm>=4.65.0
py3Dmol>=2.0.0
ipywidgets>=8.0.0
```