# 11. Medical Insurance Cost Prediction

Estimates medical insurance charges from age, sex, BMI, children, smoker status, and region. Categorical fields are encoded before linear regression.

| Item | Detail |
| --- | --- |
| Task | Regression |
| Domain | Healthcare |
| Model | Linear Regression |
| Reported result | Test R² 0.745 |
| Notebook | `Project_11_Medical_Insurance_Cost_Prediction.ipynb` |
| Data | Bundled |

Dataset is included in data/.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/11-medical-insurance-cost/Project_11_Medical_Insurance_Cost_Prediction.ipynb
```
