# Social Media Ads — Purchase Prediction Analysis

A notebook-based binary classification project using a social-media advertising dataset. The analysis explores how customer age and estimated salary relate to purchase outcomes and compares Decision Tree and Random Forest classifiers.

## Objective

Use customer demographic and salary attributes to classify whether an individual in the dataset purchased after exposure to a social-media advertisement.

## Dataset

The notebook loads `social_ads.csv` from a Kaggle dataset path. The working fields include:

- `Age`
- `EstimatedSalary`
- `Purchased` (binary target)

The dataset itself is not included in the repository; the notebook currently expects it in the Kaggle input environment.

## Workflow

1. Load the dataset and inspect shape, missing values, and target distribution.
2. Explore age and estimated-salary distributions.
3. Visualize the relationship between age, salary, and purchase label.
4. Split the data into training and testing subsets.
5. Train a baseline Decision Tree classifier.
6. Compare model depths and tune selected Decision Tree parameters using cross-validation.
7. Train and tune a Random Forest classifier.
8. Compare training and test accuracy and inspect confusion matrices and classification reports.

## Models and Evaluation

- Decision Tree Classifier
- Random Forest Classifier
- GridSearchCV with five-fold cross-validation
- Accuracy, confusion matrix, and classification report

The notebook calculates metrics interactively. No single headline performance figure is stated here because it should be taken from a fresh execution of the notebook rather than assumed from a previous kernel state.

## Run Locally

Install the core dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Download the source dataset from its Kaggle page and update the input path in the notebook. Open `social-media-analysis.ipynb` in Jupyter and execute the cells in order.

## Repository Contents

```text
.
└── social-media-analysis.ipynb
```

## Limitations

- The notebook uses only age and estimated salary as predictive features.
- A random train/test split may not represent future advertising audiences.
- Accuracy alone can hide class imbalance and unequal error costs.
- The dataset and modeling exercise do not establish causal advertising effectiveness.
- The Kaggle-specific input path must be changed for local execution.

---

**Sai Datta Putta**

[LinkedIn](https://www.linkedin.com/in/sai-datta-putta/)