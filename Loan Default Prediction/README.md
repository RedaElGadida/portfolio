# 🏦 Loan Default Prediction Model

## Project Summary

This project aims to predict the probability that a borrower will default on their loan. A **Gradient Boosting** model was trained to analyze borrower information and assess default risk, helping financial institutions minimize their losses.

## Key Findings

* **Model Performance:** The model achieved a **ROC-AUC score of 0.758**, showing a good ability to identify at-risk loans.
* **Key Risk Factors:** The most important features for predicting a loan default are the **Credit Score (`CreditScore`)**, **Income (`Income`)**, and the **Loan Amount (`LoanAmount`)**.

## Brief Methodology

1.  **Data Preparation:** Data cleaning and transformation of categorical variables (One-Hot Encoding).
2.  **Modeling:** Training and comparison of several algorithms (Random Forest, XGBoost, Gradient Boosting).
3.  **Evaluation:** Gradient Boosting was selected for its superior performance.
4.  **Analysis:** Identifying the most influential factors through feature importance analysis.

## Technologies Used

* Python
* Pandas
* Scikit-learn
* XGBoost
* Matplotlib / Seaborn
* Jupyter Notebook

## How to Run the Project

1.  Clone this repository.
2.  Install the necessary libraries:
    ```bash
    pip install pandas scikit-learn xgboost matplotlib seaborn jupyter
    ```
3.  Ensure that `train.csv` and `test.csv` are in the folder.
4.  Run the `LoanDefaultPrediction.ipynb` notebook.

---