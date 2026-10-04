# 12. Big Mart Sales Prediction

Forecasts item outlet sales from product and store attributes. Label encoding prepares categorical fields for an XGBoost regressor.

| Item | Detail |
| --- | --- |
| Task | Regression |
| Domain | Retail |
| Model | XGBoost Regressor |
| Reported result | Test R² 0.587 |
| Notebook | `Project_12_Big_Mart_Sales_Prediction.ipynb` |
| Data | Bundled |

Dataset is included in data/.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/12-bigmart-sales/Project_12_Big_Mart_Sales_Prediction.ipynb
```
