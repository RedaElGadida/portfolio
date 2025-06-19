# 📺 Customer Churn Prediction for a Streaming Platform

## Project Summary

This project analyzes customer churn for a streaming platform. A **Random Forest** model was developed to identify subscribers at high risk of cancellation, enabling proactive retention strategies.

## Key Findings

* **Model Performance:** The model achieved a **ROC-AUC score of 0.74**, demonstrating a good ability to predict churn.
* **Key Risk Factors:** The most important features for predicting churn are **Account Age (`AccountAge`)**, **Average Viewing Duration (`AverageViewingDuration`)**, and **Viewing Hours Per Week (`ViewingHoursPerWeek`)**.

## Brief Methodology

1.  **Data Preparation:** Data cleaning, one-hot encoding of categorical variables, and standardization.
2.  **Modeling:** Training and optimization of a **Random Forest** classifier with `GridSearchCV`.
3.  **Evaluation:** Measuring model performance with the ROC-AUC metric.
4.  **Analysis:** Identifying the most influential factors through feature importance analysis.

## Technologies Used

* Python
* Pandas
* Scikit-learn
* Matplotlib / Seaborn
* Jupyter Notebook

## How to Run the Project

1.  Clone this repository.
2.  Install the necessary libraries:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn jupyter
    ```
3.  Ensure that `train.csv` and `test.csv` are in the folder.
4.  Run the `Churn_Analysis.ipynb` notebook.