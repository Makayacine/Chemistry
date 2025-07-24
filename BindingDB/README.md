NB
Please note that the notebook may take up to a minute to fully render due to the large amount of whitespace output produced by PySpark when displaying DataFrame previews.

# Predicting BTK Inhibitor Potency with Machine Learning

This project demonstrates a complete machine learning workflow to predict the bioactivity (pIC50) of chemical compounds against Bruton's Tyrosine Kinase (BTK). The analysis is performed using a combination of data processing, cheminformatics, and machine learning libraries in Python.

The entire workflow is detailed in the `Binding.DB.ipynb` notebook.

---

## Core Technologies and Libraries Used

This project leverages several key Python libraries to handle data processing, feature engineering, model training, and visualization.

### Data Handling and Processing
* **PySpark (`pyspark`):** Used for the initial loading and filtering of the large BindingDB dataset. Its distributed computing capabilities are ideal for handling datasets that might be too large for in-memory processing with standard libraries.
* **Pandas (`pandas`):** The primary tool for data manipulation once the dataset is filtered down to a manageable size. It is used for creating and managing DataFrames, cleaning data, and preparing features for the machine learning model.
* **NumPy (`numpy`):** Provides support for large, multi-dimensional arrays and matrices, along with a collection of mathematical functions to operate on these arrays. It is used for numerical operations, especially in calculating metrics and handling feature arrays.

### Cheminformatics and Feature Engineering
* **RDKit (`rdkit`):** An essential open-source cheminformatics toolkit. In this project, it is used for:
    * Parsing SMILES strings into molecular objects.
    * Calculating key physicochemical descriptors (e.g., Molecular Weight, LogP, TPSA).
    * Generating Morgan fingerprints, which convert molecular structures into a numerical format suitable for machine learning models.

### Machine Learning
* **Scikit-learn (`sklearn`):** The core library for building and evaluating the predictive model.
    * `RandomForestRegressor`: The machine learning algorithm used to predict pIC50 values.
    * `train_test_split`: For partitioning the data into training, validation, and test sets.
    * `ParameterSampler`: For performing a randomized search over a grid of hyperparameters.
    * `cross_val_score`: For evaluating model performance using k-fold cross-validation.
    * `mean_squared_error`, `r2_score`: For calculating performance metrics (RMSE and R²).

### Data Visualization
* **Matplotlib (`matplotlib.pyplot`):** Used for creating static, annotated visualizations. In this notebook, it's used to generate histograms of pIC50 distribution and residual plots.
* **Seaborn (`seaborn`):** Built on top of Matplotlib, it provides a high-level interface for drawing attractive and informative statistical graphics, such as the pair plots used for initial data exploration.
* **py3Dmol:** A library for creating interactive, 3D visualizations of molecules directly within the Jupyter Notebook, used here to display the structure of the top-predicted inhibitor.

### Utilities
* **TQDM (`tqdm`):** Provides a simple and effective progress bar for long-running loops, which is particularly useful during the hyperparameter tuning phase.

---

## Project Workflow Summary

1.  **Data Ingestion:** The full BindingDB dataset is loaded using PySpark.
2.  **Data Cleaning & Filtering:** The data is filtered to retain only high-quality IC50 measurements for the human BTK target. Outliers are removed.
3.  **Feature Engineering:** SMILES strings are converted into numerical features using RDKit, including physicochemical descriptors and Morgan fingerprints.
4.  **Model Training:** A Random Forest Regressor is trained on the featurized data.
5.  **Hyperparameter Tuning:** The model's performance is optimized using a randomized search with 5-fold cross-validation.
6.  **Evaluation & Interpretation:** The final model is evaluated on a hold-out test set, and feature importances are analyzed to understand the key drivers of BTK inhibition.
7.  **Prediction:** The trained model is used to predict the pIC50 for the entire dataset, and the most potent compound is identified and visualized.

## How to Run

1.  **Install Dependencies:**
    ```bash
    pip install pyspark pandas rdkit-pypi scikit-learn matplotlib seaborn tqdm py3dmol
    ```
2.  **Download Data:** Obtain the `BindingDB_All.tsv` file from the official BindingDB website.
3.  **Run the Notebook:** Open and execute the cells in `Binding.DB.ipynb` in a Jupyter environment.

##NB the Notebook takes a minutes to load because of the pyspark 
