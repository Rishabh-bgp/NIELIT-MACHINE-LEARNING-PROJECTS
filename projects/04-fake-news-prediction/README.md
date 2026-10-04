# 04. Fake News Prediction

Classifies news articles as reliable or fake. Text is vectorized with TF-IDF and classified with logistic regression.

| Item | Detail |
| --- | --- |
| Task | Text classification |
| Domain | Natural language |
| Model | TF-IDF + Logistic Regression |
| Reported result | Test accuracy 97.9% |
| Notebook | `Project_4_Fake_News_Prediction.ipynb` |
| Data | Not bundled |

Place the Kaggle fake-news train.csv in data/train.csv before running.

Results are the scores saved in the notebook outputs. Re-run the notebook after any split or preprocessing change before treating them as current.

```bash
# from the repository root
pip install -r requirements.txt
jupyter notebook projects/04-fake-news-prediction/Project_4_Fake_News_Prediction.ipynb
```
