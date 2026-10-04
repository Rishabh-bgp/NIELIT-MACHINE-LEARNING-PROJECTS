# 08. Gold Price Prediction

Predicts the GLD price from equity, oil, silver, and currency features. A random forest regressor is fit after correlation analysis.

| Item | Detail |
| --- | --- |
| Task | Regression |
| Domain | Markets |
| Model | Random Forest Regressor |
| Reported result | Reported R² 0.989 |
| Notebook | `Project_8_Gold_Price_Prediction.ipynb` |
| Data | Bundled |

Dataset is included in data/.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/08-gold-price-prediction/Project_8_Gold_Price_Prediction.ipynb
```
