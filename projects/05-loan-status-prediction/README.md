# 05. Loan Status Prediction

Predicts loan approval from applicant income, credit history, education, and property area. Missing values are handled before training a support vector classifier.

| Item | Detail |
| --- | --- |
| Task | Binary classification |
| Domain | Finance |
| Model | Support Vector Classifier |
| Reported result | Test accuracy 83.3% |
| Notebook | `Project_5_Loan_Status_Prediction.ipynb` |
| Data | Bundled |

Dataset is included in data/.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/05-loan-status-prediction/Project_5_Loan_Status_Prediction.ipynb
```
