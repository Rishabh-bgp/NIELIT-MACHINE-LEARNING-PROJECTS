# 16. Calories Burnt Prediction

Predicts calories burnt by joining exercise and calorie tables, then training an XGBoost regressor on duration, heart rate, and body measurements.

| Item | Detail |
| --- | --- |
| Task | Regression |
| Domain | Health and fitness |
| Model | XGBoost Regressor |
| Reported result | See notebook |
| Notebook | `Project_16_Calories_Burnt_Prediction.ipynb` |
| Data | Not bundled |

Place calories.csv and exercise.csv in the data/ folder before running.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/16-calories-burnt/Project_16_Calories_Burnt_Prediction.ipynb
```
