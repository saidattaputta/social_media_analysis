# Social Media Ads — Purchase Prediction Analysis

A notebook-based classification case study using a social-media advertising dataset. The analysis explores whether customer age and estimated salary can help classify purchase outcomes, and compares a tuned Decision Tree with a Random Forest classifier.

## Objective

Build and compare baseline tree-based classifiers for the binary Purchased outcome, then interpret the results using held-out test metrics.

## Dataset

The notebook reads social_ads.csv from a Kaggle dataset path.

| Dataset attribute | Value |
|---|---:|
| Rows | 400 |
| Columns | 3 |
| Features | Age, EstimatedSalary |
| Target | Purchased |
| Non-purchase records | 257 |
| Purchase records | 143 |

The dataset is not committed to this repository. The notebook currently expects it in the Kaggle input environment.

## Results

The notebook uses a train/test split with 80 test records (52 non-purchases and 28 purchases).

### Model comparison

| Model | Training accuracy | Test accuracy |
|---|---:|---:|
| Tuned Decision Tree | 96.25% | 83.75% |
| Random Forest | 99.69% | 90.00% |

The Decision Tree GridSearchCV result reports:

- Best parameters: criterion = entropy, max_depth = 8, min_samples_split = 5
- Best cross-validation accuracy: **90.625%**
- Test accuracy: **83.75%**

The Random Forest test classification report is:

| Class | Precision | Recall | F1-score | Support |
|---|---:|---:|---:|---:|
| Not purchased (0) | 0.96 | 0.88 | 0.92 | 52 |
| Purchased (1) | 0.81 | 0.93 | 0.87 | 28 |
| **Accuracy** |  |  | **0.90** | **80** |

Random Forest's saved confusion matrix is:

\`\`\`text
[[46, 6],
 [ 2, 26]]
\`\`\`

For the purchase class, the model identifies 26 of 28 test purchases (recall 92.9%) with 6 false positives among the 52 non-purchase records. The saved notebook comparison therefore favours Random Forest on this split.

### Decision Tree depth comparison

The notebook records the following test accuracies before final parameter selection:

| Maximum depth | Train accuracy | Test accuracy |
|---:|---:|---:|
| 2 | 91.88% | 91.25% |
| 4 | 93.13% | 91.25% |
| 6 | 95.00% | 86.25% |
| 8 | 97.50% | 85.00% |

These are an earlier depth sweep and should be kept distinct from the later GridSearchCV model result of 83.75% test accuracy.

## Workflow

1. Load the 400-row dataset.
2. Inspect the purchase-class distribution.
3. Explore Age and EstimatedSalary.
4. Create training and test partitions.
5. Fit a baseline Decision Tree.
6. Compare selected tree depths.
7. Tune the Decision Tree using five-fold GridSearchCV.
8. Fit and evaluate a Random Forest.
9. Compare train/test accuracy, confusion matrices, and class-wise metrics.

## Repository Contents

- social-media-analysis.ipynb — exploration, model training, tuning, and evaluation
- README.md — project documentation

The Kaggle source CSV is not stored in this repository.

## Technology

Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, DecisionTreeClassifier, RandomForestClassifier, GridSearchCV, and Jupyter Notebook.

## Reproducing the Analysis

Install the notebook dependencies:

\`\`\`bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
\`\`\`

Download the source dataset from Kaggle and update the notebook's input path if running locally. Execute the notebook cells in order.

## Limitations

- The model uses only Age and EstimatedSalary.
- The reported metrics come from one saved train/test split of 80 records.
- The positive class contains only 28 test examples, so one or two changed predictions materially affect recall.
- Random Forest training accuracy is 99.69%, compared with 90.00% test accuracy; this gap suggests possible overfitting.
- Accuracy on a small split does not demonstrate generalization to new campaigns, audiences, or platforms.
- The dataset does not establish that seeing an advertisement caused a purchase.

---

**Sai Datta Putta**

[LinkedIn](https://www.linkedin.com/in/sai-datta-putta/)
