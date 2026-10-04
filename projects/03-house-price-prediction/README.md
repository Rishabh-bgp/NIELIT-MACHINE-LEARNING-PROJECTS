# 03. House Price Prediction

Predicts median house value with XGBoost. The notebook loads the classic Boston housing set through scikit-learn. That loader was removed in scikit-learn 1.2; use fetch_openml(name='boston', version=1, as_frame=True) or a current housing set if the import fails.

| Item | Detail |
| --- | --- |
| Task | Regression |
| Domain | Real estate |
| Model | XGBoost Regressor |
| Reported result | Test R² 0.912 |
| Notebook | `Project_3_House_Price_Prediction.ipynb` |
| Data | Not bundled |

Loaded in-notebook via sklearn.datasets.load_boston(). No CSV is bundled.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/03-house-price-prediction/Project_3_House_Price_Prediction.ipynb
```
