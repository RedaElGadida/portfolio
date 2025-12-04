# Demand Forecasting Portal  
**Multi-model time-series forecasting system with calibration & Streamlit UI**

This project is an end-to-end forecasting pipeline designed for real business operations such as demand planning, inventory management, customer budgeting, and production forecasting.

It transforms raw Excel inputs into clean, structured data, builds multiple forecast models (Baseline + Holt-Winters ML), calibrates the results, and exposes everything through a professional **Streamlit web application**.

This README explains the full logic behind the project — without requiring any dataset.

---

## Project Overview

The solution was built for use in a production environment where data quality varies and accuracy matters.  
The system includes:

### **1. Intelligent Data Ingestion**
- Automatic header detection (for messy Excel uploads)
- Cleaning and normalization of all input sheets  
- Reliable handling of mixed date formats  
- Standardization of Itemcode, Group, Customer Group, Month keys  

### **2. FACT Table Construction**
A clean, modeling-ready FACT table is created by:

- Parsing and repairing delivery dates  
- Generating consistent `Month_ym` periods  
- Separating Actuals from S&OP months  
- Imputing missing Group labels using stable Itemcode history  
- Filtering and aggregating monthly quantities  

This table forms the foundation for all forecasting models.

---

## Forecasting Models

### **Baseline Model — Seasonal Naïve (12 months)**
- Uses last year's same month value  
- Extremely stable for aggregated product demand  
- Serves as fallback if ML does not improve accuracy  

### **Holt–Winters ML Model**
The system trains an additive Holt–Winters model for each series:

- Additive trend  
- Additive seasonality  
- Optimized smoothing parameters  
- Automatic per-series selection  
- Applied only when HW beats the baseline over the last 3 evaluation months (WAPE)

### **Performance Evaluation**
Models are compared using:

- **WAPE** (Weighted Absolute Percentage Error)  
- Evaluation over the last 3 months of training data  
- Separate policies for Item Groups and Customer Groups  

This ensures the model chosen for each group is the **best performing one**, not just the most complex.

---

## 🎯 Calibration Layer (Business-Focused)

ML forecasts are **calibrated** to ensure the next-month totals remain consistent with the baseline forecast.

This step:
- Prevents unrealistic jumps in total demand  
- Preserves ML’s internal mix between groups  
- Guarantees that the final number is operationally trustworthy  

Total calibration is crucial for real-world use, especially in supply chain environments.

---

## 🔽 Itemcode Allocation Engine

Once Group-level forecasts are ready, they are allocated down to Itemcode level using a hierarchical top-down model.

Allocation uses this fallback chain:

1. **Last 3 months** of history  
2. **Last 12 months**  
3. **Lifetime** data  
4. **Equal split** fallback  

This ensures:
- Every item receives a fair and data-driven allocation  
- All allocations sum back to the group total (±1 rounding)  
- Zero leakage or inconsistencies  

---

## 🖥️ Streamlit App (User Interface)

The Streamlit interface provides an accessible way to explore the forecast results:

### What the app displays:
- Latest actual month  
- Next forecast month  
- Item Group forecasts  
- Customer Group forecasts  
- Baseline, ML, and calibrated modes  
- Model selection details  
- Downloadable forecast tables  
- Historical charts for every group  

The interface is designed for non-technical users while leveraging a complex forecasting engine underneath.

---

## 📐 Accuracy Expectations

Based on evaluation and typical market stability:

| Forecast Type | Expected WAPE |
|---------------|----------------|
| Product Demand (Item Groups) | **15–20%** |
| Customer Demand (Customer Groups) | **18–25%** |

These ranges were consistently achieved during development.

---

## 🛠️ Technologies Used

- **Python** (Pandas, NumPy)  
- **Statsmodels** (Holt–Winters Exponential Smoothing)  
- **Streamlit** (Web application)  
- **OpenPyXL** (Excel ingestion)  
- **Matplotlib** (Visualizations)  

