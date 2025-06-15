Credit Card Fraud Detection
Project Overview
This project demonstrates a complete machine learning workflow to identify fraudulent credit card transactions within a highly imbalanced dataset. The primary goal is to build and evaluate several classification models, employing various techniques to handle the class imbalance and determine the most effective and practical solution for fraud detection.

The analysis progresses from a baseline model to more advanced techniques, showcasing a methodical approach to problem-solving in a real-world scenario.

The Challenge: Class Imbalance
The dataset presents a classic and significant challenge in machine learning: severe class imbalance. Fraudulent transactions represent only 0.172% of the total transactions. A naive model trained on this data would likely achieve high accuracy by simply classifying all transactions as legitimate, thereby failing its primary purpose of detecting fraud.

This project's core focus is to implement strategies that address this imbalance to build a model with high practical value, focusing on metrics like Precision and Recall rather than accuracy alone.

Dataset
The project utilizes the "Credit Card Fraud Detection" dataset, available on Kaggle.

Source: Kaggle Credit Card Fraud Detection Dataset
Content: The dataset contains transactions made by European cardholders over two days in September 2013.
Features: To protect user privacy, most features (V1 through V28) are the result of a Principal Component Analysis (PCA) transformation. The only features that have not been transformed are Time and Amount.
Methodology
The project followed a structured, end-to-end machine learning workflow:

Exploratory Data Analysis (EDA): The dataset was analyzed to understand its structure, feature distributions, and the extent of the class imbalance.

Data Preprocessing: The Time and Amount columns were scaled using StandardScaler from scikit-learn to ensure all features were on a comparable scale.

Handling Class Imbalance: Two primary techniques were implemented and compared on the training data:

Random Undersampling: Randomly removing samples from the majority class (legitimate transactions) to create a balanced dataset.
SMOTE (Synthetic Minority Over-sampling Technique): Creating new, synthetic samples of the minority class (fraudulent transactions) to balance the dataset without losing information from the majority class.
Modeling and Evaluation: Three distinct models were trained and evaluated to find the best-performing combination of data strategy and algorithm:

Model 1: Logistic Regression with Random Undersampling
Model 2: Logistic Regression with SMOTE
Model 3: Random Forest with SMOTE
Results & Key Findings
The models were evaluated based on their ability to correctly identify fraud (Recall) while minimizing incorrect flags on legitimate transactions (Precision).

Model	Balancing Technique	Precision (Fraud)	Recall (Fraud)	F1-Score (Fraud)
Logistic Regression	Random Undersampling	0.04	0.92	0.07
Logistic Regression	SMOTE	0.06	0.92	0.11
Random Forest	SMOTE	0.82	0.82	0.82

Exporter vers Sheets
SMOTE proved superior to Random Undersampling. While both techniques produced models with an excellent recall of 92%, SMOTE improved precision by 50% (from 4% to 6%), resulting in fewer false positives.
The Random Forest model trained on SMOTE data delivered a massive leap in performance. It achieved a highly balanced and practical result with both precision and recall at 82%.
Final Model Performance
The final and best-performing model (Random Forest with SMOTE) is the recommended solution. While its recall (82%) is slightly lower than the baseline models (92%), its precision (82%) is dramatically higher. This represents a far more practical and reliable model for a real-world application, as it significantly reduces the number of legitimate customers whose transactions would be incorrectly flagged as fraudulent.

Technologies Used
Language: Python
Libraries:
Pandas & NumPy (Data Manipulation)
Scikit-learn (Modeling & Preprocessing)
Imbalanced-learn (SMOTE)
Matplotlib & Seaborn (Data Visualization)
Environment: Jupyter Notebook / VS Code
How to Run This Project
Clone the repository:
Bash

git clone https://github.com/your-username/your-repo-name.git
Install dependencies: It is recommended to create a requirements.txt file. You can generate one using:
Bash

pip freeze > requirements.txt
Then, install the required packages:
Bash

pip install -r requirements.txt
Run the notebook: Open the Credit_Card_Fraud_Detection.ipynb file in Jupyter Notebook, JupyterLab, or Visual Studio Code and run the cells sequentially.
Future Improvements
Hyperparameter Tuning: Use GridSearchCV or RandomizedSearchCV to fine-tune the Random Forest model's parameters for potentially even better performance.
Advanced Models: Experiment with gradient boosting models like XGBoost or LightGBM, which often excel on tabular data.
Feature Engineering: Although the features are anonymized, the Time feature could be converted into cyclical features like 'HourOfDay' to see if it improves model performance.