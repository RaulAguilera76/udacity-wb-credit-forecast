# Forecasting Next-Year Private Sector Credit Growth (World Bank)

**Objective.** Predict next-year growth of domestic credit to the private sector (annual %) for COL using a compact macro feature set (inflation, lending/real rates, broad money, unemployment, population).

## Data
World Bank Databank (annual). Files in data/raw/:
credit_private_growth.csv — target (YoY % from FS.AST.PRVT.GD.ZS)
inflation_cpi.csv — CPI YoY (from FP.CPI.TOTL)
lending_rate.csv — FR.INR.LEND
real_interest.csv — FR.INR.RINR
broad_money.csv — FM.LBL.BMNY.GD.ZS
unemployment.csv — SL.UEM.TOTL.NE.ZS
(optional) population_growth.csv — SP.POP.GROW

## Method (CRISP-DM)
1. **EDA:** time-series plots and quick correlations.
2. **Features:** contemporaneous variables at t; target is credit growth at t+1.
3. **Models:** Linear Regression, Ridge, Lasso, Random Forest.
4. **Evaluation:** time-aware split (80/20). Metrics: **MAE**, **RMSE**, **MAPE**.
5. **Scenario:** forecast next-year credit growth using the latest available year.

## How to Run
Open and run all cells in: udacity-wb-credit-forecast/notebooks/SIMPLE_Udacity_CreditForecast.ipynb

Outputs are saved to figures/:
pred_vs_actual.png
feature_importance.png
metrics_table.csv and summary_metrics.csv

## Results
**Best model:** RandomForest
**RMSE:** 7.71 | **MAE:** 6.5 | **MAPE:** 162.93%
**Scenario:** Using 2022 macro data for COL, the model predicts **4.66%** next-year credit growth.

## Interpretation for Banking
Higher **lending/real rates** and **inflation** typically depress next-year credit growth (tighter monetary stance), while **broad money** is usually positively associated with future credit (liquidity). Use the point forecast with risk bands and policy judgment for **credit budget sizing**, **pricing**, and **liquidity planning**.

## Notes & Limitations
Annual data ⇒ small samples; regime changes and shocks may not be captured. **MAPE can be very high** when the target is near zero; prefer MAE/RMSE in that case. Panel data or higher-frequency inputs would likely improve accuracy.

## Environment
pandas, numpy, scikit-learn, matplotlib.
