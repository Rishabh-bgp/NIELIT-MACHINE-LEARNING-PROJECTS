# 14. Parkinson's Disease Detection

Detects Parkinson's disease from biomedical voice measurements. Features are standardized before training a support vector classifier.

| Item | Detail |
| --- | --- |
| Task | Binary classification |
| Domain | Healthcare |
| Model | SVC with StandardScaler |
| Reported result | Test accuracy 87.2% |
| Notebook | `Project_14_Parkinson's_Disease_Detection.ipynb` |
| Data | Not bundled |

Place the UCI/Kaggle parkinsons.csv file in data/parkinsons.csv before running.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/14-parkinsons-detection/Project_14_Parkinson's_Disease_Detection.ipynb
```
