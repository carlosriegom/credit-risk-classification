# HELOC Credit Repayment Behavior Prediction

**Authors:** Pablo Rodríguez Soria, Ángel Visedo Tomás and José Carlos Riego

This project applies Machine Learning techniques to predict whether Home Equity Line of Credit (HELOC) applicants will repay their loans.

## Project Description

The main objective is to develop and compare various classification models to identify default risk, serving as a support tool for lending decisions in financial institutions.

A HELOC is a type of credit secured by the homeowner's property, which typically offers lower interest rates than other loans.

## The Dataset

The dataset includes variables related to the customers' credit history and their FICO Score.

### Main Variables

- **ExternalRiskEstimate:** External risk measure.
- **NetFractionRevolvingBurden:** Ratio of current credit usage vs. maximum allowed.
- **NumSatisfactoryTrades:** Number of satisfactory trades.
- **Output Variable (RiskPerformance):** Indicates if the customer paid as negotiated (0 = Paid, 1 = Defaulted).

## Data Preprocessing

To ensure training quality, the following tasks were performed:

- **Special characters treatment:** Records with codes -7, -8, and -9 (missing information or registry records) were removed as they did not provide significant value.
- **Missing values:** Rows with null values were discarded after verifying that models supporting them did not outperform others.
- **Outlier Analysis:** Outliers were kept as they provide valuable information about the studied phenomenon and were not considered scientifically invalid.
- **Variable Selection:** `MSinceOldestTradeOpen` and `NumTotalTrades` were discarded due to low sensitivity and strong correlation with other variables.

## Evaluated Models

Various classification algorithms were tested, optimizing their hyperparameters via cross-validation to maximize the F1-score:

1.  **Logistic Regression (LR):** No adjustment hyperparameters.
2.  **K-Nearest Neighbors (kNN):** Optimal value of 71 neighbors.
3.  **Decision Tree (DT):** With a minimum impurity decrease of 0.0045.
4.  **Random Forest (RF):** Configured with 10 trees and a maximum depth of 5.
5.  **Support Vector Machines (SVM):** Cost C = 10.
6.  **Naive Bayes (NB):** Based on Bayes' theorem and variable independence.
7.  **Gradient Boosting (GBC):** Sequential models for error correction.
8.  **Multi-Layer Perceptron (MLP):** Neural network with 3 hidden layers of 4 neurons each.

## Results and Conclusions

The Multi-Layer Perceptron (MLP) model was selected as the best after comparative analysis.

- **MLP Performance:** Achieved an F1-score of 0.749 in cross-validation and an Area Under the ROC Curve (AUC) of 0.797.
- **Key Metrics:** F1-score and sensitivity were prioritized to balance the identification of high-risk customers and minimize unnecessary rejection of solvent customers.
- **Simplicity vs. Accuracy:** Although the MLP was superior, simpler models like Logistic Regression or Random Forest showed good performance and might be preferable if greater interpretability is required.

## **Execution instructions**

All code is included in `assignment.ipynb` notebook.

For installing dependencies, run:

```bash
conda env create -f environment.yml
```
