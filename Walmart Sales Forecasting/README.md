# Walmart Sales Forecasting

## Project Overview

This project demonstrates a comprehensive workflow for time series forecasting, aimed at accurately predicting weekly sales for Walmart stores. The analysis compares three distinct methodologies: a classical statistical model (SARIMA), a modern automated library (Prophet), and a supervised machine learning approach (XGBoost) to determine the most effective strategy.

## The Challenge: Time-Dependent Patterns

The primary challenge in sales forecasting is effectively modeling complex time-based patterns, including:

-   **Trend:** The long-term increase or decrease in sales.
-   **Seasonality:** The repeating patterns within a year, especially significant spikes during holiday seasons.
-   **External Factors:** The direct impact of holidays and promotional markdowns on sales performance.

## Dataset

This project utilizes the "Walmart Recruiting - Store Sales Forecasting" dataset from Kaggle. It contains historical sales data for 45 Walmart stores across various departments.

-   `train.csv`: Contains the core training data, including Store, Dept, Date, and Weekly\_Sales.
-   `features.csv`: Provides external data like Temperature, Fuel Price, and whether the week is a holiday.
-   `stores.csv`: Contains metadata about each store, such as its type and size.

## Methodology

The project followed a structured, end-to-end workflow:

1.  **Exploratory Data Analysis (EDA):** The datasets were loaded, merged, and visualized to identify underlying trends, seasonality, and correlations.
2.  **Time Series Decomposition & Stationarity Testing:** The aggregated time series was formally decomposed, and the Augmented Dickey-Fuller (ADF) test was used to check for stationarity before classical modeling.
3.  **Modeling & Evaluation:** Three distinct models were trained and evaluated using Mean Absolute Error (MAE) as the primary metric:
    * **Model 1: SARIMA** - A statistical benchmark model to capture seasonality.
    * **Model 2: Prophet** - An automated forecasting library by Meta, incorporating holiday effects.
    * **Model 3: XGBoost** - A supervised machine learning model using a rich set of engineered features (lags, rolling averages, date components).

## Final Performance Results

Here is a summary of the performance for each model, with the Mean Absolute Error (MAE) as the key metric for comparison.

**SARIMA Model (Benchmark)**
* **Methodology:** Statistical
* **Mean Absolute Error (MAE):** $3,435,074

**Prophet Model**
* **Methodology:** Automated Library
* **Mean Absolute Error (MAE):** $3,737,351

**XGBoost Model (Winner)**
* **Methodology:** Machine Learning
* **Mean Absolute Error (MAE):** **$1,408,513**

---

## Verdict

The **supervised machine learning approach using XGBoost and engineered features was the most effective strategy**, delivering a forecast that was more than twice as accurate as the other models.

This demonstrates the power of converting a time series problem into a feature-rich regression problem. While SARIMA provided a solid statistical benchmark, the ability of XGBoost to learn complex, non-linear relationships from features like sales lags and rolling averages allowed it to capture the underlying dynamics of the sales data with far greater precision. This model would provide the most business value for applications such as inventory planning and revenue forecasting.

## Technologies Used

-   **Language:** Python
-   **Libraries:**
    -   Pandas & NumPy
    -   Scikit-learn
    -   Statsmodels (for SARIMA)
    -   Prophet
    -   XGBoost
    -   Matplotlib & Seaborn
-   **Environment:** Jupyter Notebook / VS Code

## How to Run This Project

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    ```
2.  **Install dependencies:**
    It is recommended to create and use a `requirements.txt` file.
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the notebook:**
    Open the `Sales-Forecasting-Project.ipynb` file in Jupyter Notebook, JupyterLab, or Visual Studio Code and run the cells sequentially.

## Future Improvements

-   **Hyperparameter Tuning:** Use `GridSearchCV` or similar techniques to fine-tune the XGBoost model's parameters for potentially even better performance.
-   **Expanded Feature Engineering:** Incorporate more features from the `features.csv` and `stores.csv` files, such as `CPI`, `Unemployment`, and store `Type`/`Size`.
-   **Model Deployment:** Deploy the trained XGBoost model as a simple API using a framework like Flask or FastAPI to predict sales for a given week.