# 🌍 GHG Emissions Predictive Analysis Model

## 📌 Problem Statement
The global greenhouse gas (GHG) emissions problem has been under extensive research for decades, aiming to find ways to reduce the GHG effect by *2030*.  
This project answers an important question:

> *How can we utilize historical GHG emission records to predict future emissions?*

Using historical data from *1990–2018, this project develops a **machine learning model* to forecast GHG emissions for any country, enabling policymakers to test climate scenarios and plan strategies for emission reduction.

---

## 📂 Dataset Information

- *Title:* ghg-emissions.csv  
- *Size:* 37.2 KB  
- *Date Range:* 1990–2018  
- *Source Organization:* World Resources Institute  
- *Source:* [Climate Watch Historical GHG Emissions Data](https://www.climatewatchdata.org/ghg-emissions) (CAIT, FAO, OECD/IEA)  
- *License:* [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)  

*Columns:*
| Column Name       | Type   | Description |
|-------------------|--------|-------------|
| Country/Region  | string | Country name |
| unit            | string | Measurement unit – MtCO₂e |
| 1990...2018   | float  | Emissions for each year |
| Total Emissions | float  | Sum of emissions from 1990–2018 |

---

## 🧹 Data Cleaning

- *Missing Values:*  
  Found in 1990 column for Namibia, Palau, Micronesia, and Marshall Islands.  
  These were replaced using verified external data sources:
  - Namibia → 10.5 MtCO₂e  
  - Palau → 0.22 MtCO₂e  
  - Micronesia → 0.31 MtCO₂e  
  - Marshall Islands → 0.25 MtCO₂e

- *Actions Taken:*  
  - Replaced "FALSE" values with actual numbers  
  - Saved cleaned dataset as CSV  
  - Uploaded to Google Colab for analysis  

---

## 📊 Exploratory Data Analysis (EDA)

- Interactive dropdown to view individual country trends.
- Highest emitters: *China, **United States, **India, **Russia*.
- These countries account for *over 90%* of global emissions since 1990.
- Visualized emissions trends and total emissions over time.

---

## 🤖 Model Development

*Objective:* Predict next-year GHG emissions for each country.

*Features Used:*
- lag_1: Previous year's emissions
- rolling_mean_3: 3-year rolling average
- year: The target year

*Model Choice:*  
- *Random Forest* – best performance for non-linear trends, robust to outliers, minimal tuning required.

*Train/Test Split:*
- Last 20% of years for each country → test set (mimics real-world forecasting).

*Evaluation Metrics:*
- *RMSE* – Average prediction error in MtCO₂e  
- *R² Score* – Variance explained by the model

---

## 📈 Model Performance

| Model          | RMSE  | R²   | Runtime |
|----------------|-------|------|---------|
| Random Forest  | *412* | *0.91* | 2 min   |
| ARIMA          | 587   | 0.82 | 30 sec  |
| Prophet        | 498   | 0.87 | 5 min   |

- *Best Case:* Germany (R² = 0.96)  
- *Worst Case:* Small Island Nations (R² = 0.62)  
- *Global Average Error:* ±412 MtCO₂e

---

## 📊 Time Series Analysis Dashboard

The dashboard includes:
- Rolling mean & standard deviation (5-year window)
- Raw time series plots
- Autocorrelation analysis
- Trend & seasonality decomposition

This helps visualize how historical emissions drive future predictions.

---

## 🎯 Practical Applications

- *Policy Planning:* Predict emissions for upcoming years.
- *Progress Tracking:* Compare actual vs. predicted values.
- *Scenario Testing:* Simulate the effect of emission reduction programs.

---

## ⚠ Limitations

- *Short-Term Forecasting:* Works best for 1–5 year predictions.
- *Country-Specific Trends:* Patterns differ widely by country.
- *Data Dependency:* Relies on accurate historical data.

---

## 🚀 Future Work

- Integrate *GDP & population* as predictors.
- Build *API* for real-time policy testing.
- Add *uncertainty quantification* to predictions.

---
