# 01. Rock vs Mine Prediction

Classifies sonar returns as rock or mine from 60 frequency-band features. The notebook treats the problem as binary classification and evaluates logistic regression on a held-out split.

| Item | Detail |
| --- | --- |
| Task | Binary classification |
| Domain | Signal processing |
| Model | Logistic Regression |
| Reported result | Test accuracy 76.2% |
| Notebook | `Project_1_Rock_vs_Mine_Prediction.ipynb` |
| Data | Bundled |

Dataset is included in data/.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/01-rock-vs-mine/Project_1_Rock_vs_Mine_Prediction.ipynb
```
