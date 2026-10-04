# 19. Breast Cancer Classification

Classifies tumours as malignant or benign from the Wisconsin diagnostic features. The notebook loads the set through scikit-learn; the original CSV is also bundled for local inspection.

| Item | Detail |
| --- | --- |
| Task | Binary classification |
| Domain | Healthcare |
| Model | Logistic Regression |
| Reported result | Test accuracy 93.0% |
| Notebook | `Project_19_Breast_Cancer_Classification_using_Machine_Learning.ipynb` |
| Data | Bundled |

The notebook uses sklearn.datasets.load_breast_cancer(). data/wisconsin_breast_cancer.csv is the same public table, previously stored at the repository root as data.csv.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/19-breast-cancer-classification/Project_19_Breast_Cancer_Classification_using_Machine_Learning.ipynb
```
