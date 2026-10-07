# Car Price Prediction — Linear Regression Notebook

> A recorded tabular regression experiment, with its data and reproduction limits stated.

[Task_3.ipynb](Task_3.ipynb) estimates `Selling_Price` from vehicle attributes using label encoding,
standardization and linear regression. It includes data inspection, a train/test split,
evaluation and one example prediction. This repository is a notebook, not a deployed pricing API.

## Inspect and reproduce

Open the notebook on GitHub to read the saved outputs. To execute locally, use Python and Jupyter:

```sh
python3 -m venv .venv
.venv/bin/python -m pip install jupyterlab pandas numpy matplotlib seaborn scikit-learn
.venv/bin/python -m jupyter lab Task_3.ipynb
```

The input CSV is **not included**. Obtain the matching `car data 2.csv`, replace `file_path` in
the notebook with its location, then restart the kernel and run the cells in order. The checked-in
path points to a previous author's machine and cannot work unchanged on another computer.
Dependencies are not pinned; this installation command supplies the imported packages rather than
a reproduced historical environment.

## Data and workflow

| Role | Columns / operation |
|---|---|
| Target | `Selling_Price` |
| Numeric inputs | `Year`, `Present_Price`, `Driven_kms`, `Owner` |
| Encoded inputs | `Car_Name`, `Fuel_Type`, `Selling_type`, `Transmission` |
| Missing values | Median for kilometres; mode for fuel type |
| Split | 80% train / 20% test, `random_state=42` |
| Model | StandardScaler fitted on training inputs, then LinearRegression |
| Outputs | MSE, R² and one sample price prediction |

The saved evaluation reports **MSE 3.5370204238** and **R² 0.8464540624**. These are historical
notebook outputs inspected on 7 October 2026; the experiment was not rerun because the CSV is
absent.
The recorded sample predicts about 5.5418 in the dataset's price units. Currency/unit definitions
are not supplied in this repository, so that value should not be presented as a market quotation.

## Interpretation and limitations

Label encoding treats categories as numeric values for this model. Encoders are fitted before the
split; the notebook does not establish performance on unseen categories or independent market data.
There is one saved split, no cross-validation report, no automated tests, no dependency lockfile
and no serialized trained model. Dataset provenance and licence must be established separately.

The notebook is useful for inspecting a complete regression exercise. Reproducing its numbers
requires the same data and compatible versions; a saved output is not a fresh verification.
