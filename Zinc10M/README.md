
# Zinc10M QSAR Pipeline

A reproducible end-to-end Quantitative Structure–Activity Relationship (QSAR) workflow to predict molecular lipophilicity (log P) for millions of compounds from the ZINC15 database using 2D descriptors and circular fingerprints.



## 📋 Contents

- **Zinc10MQSAR.ipynb**  
  Main Jupyter notebook implementing:
  1. Data ingestion via PySpark  
  2. SMILES parsing & RDKit molecule construction  
  3. ECFP4 fingerprint generation  
  4. Train/test split & 5-fold cross-validation  
  5. Random Forest regression modelling  
  6. Performance evaluation (RMSE, R²)  
  7. Feature‐importance analysis  
  8. Exploratory plots & descriptor–log P correlations  

- **data/**
  - `zinc15_10M_2D.csv` (10 million SMILES + experimental log P)  
  - *Optional:* smaller sample datasets for rapid prototyping

- **requirements.txt**  
  Pinning critical Python dependencies.

---

## 🛠️ Installation

1. **Clone this repo**  
   ```bash
   git clone https://github.com/Makayacine/Chemistry.git
   cd Zinc10M
````

2. **Create & activate a virtual environment**

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Install RDKit**
   Follow the instructions for your platform from the [RDKit documentation](https://www.rdkit.org/docs/Install.html).

---

## 🗄️ Data Preparation

1. Download or place your ZINC15 CSV file (`zinc15_10M_2D.csv`) under `data/`.
2. If you wish to work on a smaller subset, either:

   * Modify the sampling fraction in the notebook, or
   * Prepare a pre-sampled CSV (e.g. `data/zinc10k_sample.csv`).

---

## 🚀 Usage

1. Launch JupyterLab or Jupyter Notebook:

   ```bash
   jupyter lab
   ```
2. Open and run **Zinc10MQSAR.ipynb** from top to bottom.
3. Inspect outputs in each section:

   * Correlation heatmap of traditional descriptors
   * Scatter plots (e.g. ring count vs. log P)
   * Cross-validation performance curves
   * Final test-set metrics & feature importance

---

## 🧩 Notebook Structure

1. **Setup & Imports**
   Load PySpark, pandas, RDKit, scikit-learn, seaborn, matplotlib.

2. **Data Loading**
   Read large CSV via Spark; sample a manageable subset to pandas.

3. **SMILES → RDKit Molecules**
   Parse each SMILES string, filter out invalid entries.

4. **Descriptor Calculation**

   * Compute traditional 2D descriptors (MolWt, TPSA, H-bond donors/acceptors, ring count, etc.)
   * Generate ECFP4 (Morgan) fingerprints

5. **Exploratory Data Analysis**

   * Correlation matrix
   * Key scatter plots

6. **Modeling Pipeline**

   * Train/test split
   * 5-fold cross-validation
   * Random Forest regressor fitting & hyperparameter tuning

7. **Evaluation & Interpretation**

   * Compute RMSE & R² on test set
   * Plot feature importances
   * Summarize main physicochemical trends

---

## 📈 Results

* **Descriptor Correlations**

  * MolWt ⇢ strong positive with log P (ρ ≈ 0.91)
  * TPSA/H-bond counts ⇢ moderately negative
  * Ring count ⇢ weak positive

* **Model Performance**

  * RMSE ≈ 0.60 log P units
  * R² ≈ 0.80

* **Key Substructures**
  Top ECFP4 bits reveal which local atom environments most drive lipophilicity predictions.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!
Feel free to submit a Pull Request or open an Issue in this repository.


