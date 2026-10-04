# 17. Spam Mail Prediction

Classifies email text as ham or spam. Messages are vectorized with TF-IDF and classified with logistic regression.

| Item | Detail |
| --- | --- |
| Task | Text classification |
| Domain | Natural language |
| Model | TF-IDF + Logistic Regression |
| Reported result | Test accuracy 96.6% |
| Notebook | `Project_17_Spam_Mail_Prediction_using_Machine_Learning.ipynb` |
| Data | Bundled |

Dataset is included in data/.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/17-spam-mail/Project_17_Spam_Mail_Prediction_using_Machine_Learning.ipynb
```
