# Medical Insurance Cost Prediction

## Project Overview

This project uses machine learning to predict individual medical insurance charges based on personal and insurance-related features. The analysis and model development are documented in the Jupyter Notebook `Insurance_prediction.ipynb`.

The notebook follows a typical data science workflow:
1. Load and explore the insurance dataset.
2. Clean and preprocess the data.
3. Explore relationships between features and insurance charges.
4. Split the data into training and testing sets.
5. Train a Linear Regression model.
6. Evaluate the model using the R-squared and adjusted R-squared scores.

## Dataset

The notebook loads the dataset from a file named `insurance.csv`. Place this file in the same directory as the notebook before running it.

The columns used in the analysis include:

| Column | Description |
|---|---|
| `age` | Age of the insured person |
| `sex` | Sex of the insured person |
| `bmi` | Body Mass Index |
| `children` | Number of children/dependants covered |
| `smoker` | Whether the person smokes |
| `region` | Residential region |
| `charges` | Medical insurance cost (prediction target) |

## Technologies and Libraries

- Python
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib
- Seaborn
- SciPy
- Scikit-learn

## Setup and Installation

1. Clone or download this project.
2. Make sure Python is installed.
3. (Recommended) Create and activate a virtual environment.
4. Install the required libraries:

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter
```

5. Put `insurance.csv` in the project directory.
6. Start Jupyter Notebook:

```bash
jupyter notebook
```

7. Open `Insurance_prediction.ipynb` and run the cells in order.

## Project Workflow

### 1. Exploratory Data Analysis (EDA)

The notebook examines the dataset's dimensions, sample records, data types, descriptive statistics, missing values, and columns. It uses histograms, count plots, box plots, and a correlation heatmap to explore the data.

### 2. Data Cleaning and Preprocessing

The notebook:
- Creates a copy of the original dataset.
- Removes duplicate records.
- Converts `sex` into a numeric feature (`male_female`).
- Converts `smoker` into a numeric feature (`is_smoker`).
- Renames the encoded columns.
- Applies one-hot encoding to `region`.
- Creates BMI categories (Underweight, Normal, Overweight, and Obese) and one-hot encodes those categories.
- Standardizes `age`, `bmi`, and `children`.
- Examines feature relationships with insurance charges using Pearson correlation and chi-square tests.

### 3. Model Training

The target variable is `charges`. The remaining selected columns are used as input features.

The data is split into:
- 80% training data
- 20% testing data

The split uses `random_state=42` for reproducibility. A Linear Regression model is then trained on the training data.

### 4. Model Evaluation

The notebook generates predictions for the test set and calculates:
- **R-squared (R²):** measures the proportion of variation in insurance charges explained by the model.
- **Adjusted R-squared:** adjusts R² based on the number of input features and observations.

The notebook displays the adjusted R-squared as a percentage. Run the notebook to obtain the actual evaluation values for your dataset.

## Repository Structure

```text
.
├── Insurance_prediction.ipynb   # Data analysis, preprocessing, model training and evaluation
├── insurance.csv                # Input dataset (add this file)
└── README.md                    # Project documentation
```

## Notes

- The notebook expects the dataset file to be named exactly `insurance.csv`.
- Run notebook cells from top to bottom because later steps depend on variables created earlier.
- The reported model performance depends on the dataset and the preprocessing performed.
- For a more rigorous evaluation, fit preprocessing steps such as `StandardScaler` using only the training data (ideally through a Scikit-learn Pipeline). In the current notebook, scaling is performed before the train-test split, so information from the test set can influence the scaling parameters.
- The BMI category features are derived from BMI, so they contain information already represented by the original `bmi` feature.

## Author

G Dinesh
