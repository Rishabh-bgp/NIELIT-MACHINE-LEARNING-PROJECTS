# 09. Credit Card Fraud Detection

Detects fraudulent card transactions on a heavily imbalanced set. The notebook under-samples the majority class before training logistic regression.

| Item | Detail |
| --- | --- |
| Task | Imbalanced classification |
| Domain | Finance |
| Model | Logistic Regression with under-sampling |
| Reported result | Test accuracy 93.9% |
| Notebook | `Project_9_Credit_Card_Fraud_Detection.ipynb` |
| Data | Not bundled |

Place the credit-card fraud CSV at data/credit_data.csv. The public Kaggle file is large and is not stored in this repository.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/09-credit-card-fraud-detection/Project_9_Credit_Card_Fraud_Detection.ipynb
```
