# Forecasting Private-Sector Credit Growth (Colombia) with World Bank Data

**Question.** Can a compact set of macro indicators explain and forecast next-year private credit growth?  
**Data.** Annual World Bank indicators for Colombia: inflation (CPI), lending rate, real interest rate, broad money, unemployment, and (optional) population growth.  
**Method.** Time-aware split (80/20, oldest→newest) and scikit-learn pipelines: Linear, Ridge, Lasso, RandomForest. Metrics: MAE, RMSE, MAPE. Target = YoY private-sector credit growth at *t+1*.

![Actual vs Predicted](../cred_vs_actual.png)

## 1) Most important features & meaning
Across models, **interest-rate variables (lending and real rates)** and **inflation** carry the largest signal and have **negative** association with next-year credit growth—consistent with tighter monetary stance depressing credit. **Broad money** tends to be **positively** related to future credit (liquidity conditions). Unemployment adds weaker but complementary information.

## 2) Unusual/creative insights
- The **direction** of effects aligns with banking intuition, but magnitudes vary across regimes; this suggests using rolling or time-varying models in production.  
- **Near-zero credit growth years** distort percentage errors (MAPE); absolute metrics (MAE/RMSE) are more informative for this target.

## 3) Model accuracy
Best model: **RandomForest**  
- **RMSE:** 7.71  
- **MAE:** 6.50  
- **MAPE:** 162.93% (inflated by near-zero denominators)

Interpretation: the model captures broad moves in credit growth with single-digit absolute error (pp). For bank planning, this supports scenario ranges rather than point bets.

## 4) Scenario (policy/FP&A style)
Using **latest available macro data for 2022 (COL)**, the model projects **4.66%** private-sector credit growth for the following year.  
**Implication:** with higher rates and CPI in 2022, the outlook moderates; liquidity (broad money) partly offsets.

---

*Limitations:* annual frequency and small sample; structural breaks and credit-supply constraints are not fully captured.  
*Environment:* Python 3, pandas, numpy, scikit-learn, matplotlib. See repository for code, figures and requirements.

"Add blog for Githubpages"
