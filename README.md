# -Retail-demand-forecasting-Project
An end-to-end retail demand forecasting engine leveraging temporal lag features, rolling statistics, and Random Forest ensembles to optimize multi-store inventory. Deployed via FastAPI REST endpoints and an interactive Streamlit dashboard to simulate multi-horizon demand scenarios and prevent stockouts.
# Retail Demand Forecasting and Inventory Optimization System

### 1. Project Overview
In modern retail operations, accurate demand forecasting is critical for streamlining supply chain logistics, optimizing working capital, and preventing costly stockouts or inventory overstocking. This project delivers an end-to-end machine learning system designed to predict store- and product-level sales across multiple retail locations. By translating raw historical transaction records into structured predictive features, the platform enables retail managers to make data-backed inventory replenishment decisions.

### 2. Data Pipeline & Feature Engineering
The pipeline processes multi-store historical sales datasets and extracts strong temporal signals to capture seasonal consumption behaviors:
* **Autoregressive Lags:** Integrates 1-day (t-1) and 7-day (t-7) historical demand lags to monitor short-term sales momentum and weekly cyclicality.
* **Rolling Window Statistics:** Computes 7-day moving averages and moving standard deviations to reflect real-time demand levels and local volatility.
* **Calendar & Promotional Signals:** Encodes calendar attributes (day of week, month, day of year) along with binary flags for weekend traffic and marketing promotions.

### 3. Machine Learning Modeling & Evaluation
To eliminate lookahead bias, the data was partitioned chronologically into training and out-of-time evaluation windows. A Random Forest Regressor was trained and evaluated against baseline methods, including naive lag persistence and simple moving averages. The model delivered superior accuracy across standard regression metrics:
* **Mean Absolute Error (MAE):** ~4.13 to 4.25 units.
* **Root Mean Squared Error (RMSE):** ~5.25 to 5.50 units.
* **Mean Absolute Percentage Error (MAPE):** Maintained below 8.3%, demonstrating high stability against sudden demand shifts.

### 4. Deployment Architecture & User Interface
The system bridges machine learning modeling with practical software deployment through two main components:
* **FastAPI Backend:** Encapsulates the serialized model artifacts into a high-performance RESTful API endpoint (/predict), allowing external software to request real-time single-day or multi-day forecasts.
* **Streamlit Web Dashboard:** Provides an interactive interface where store planners can select store branches and product lines, visualize historical demand trends with interactive charts, generate 1-day to 30-day automated forecasts, and download forecast summaries as CSV files for inventory planning.

### 5. Business Impact
By combining time-series feature engineering, machine learning regression, and accessible web deployment, this project provides a production-ready solution that helps retailers reduce forecasting errors, optimize inventory reorder cycles, and safeguard revenue.
