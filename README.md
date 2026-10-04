# NIELIT Machine Learning Projects

Nineteen end-to-end machine learning projects: classification, regression, clustering, and recommendation. Each project is a runnable Jupyter notebook with a documented pipeline, from data loading and exploratory analysis through training and evaluation.

The notebooks were originally written for Google Colab and stored in a single flat directory. They are now grouped by project, local dataset paths replace `/content/...` mounts, and bundled tables sit beside the notebook that uses them.

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-classical%20ML-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg)](LICENSE)

## Catalog

Reported scores are the values saved in each notebook. They are not a fresh benchmark. Re-run a notebook before citing a number.

| # | Project | Task | Model | Reported result | Data |
| --- | --- | --- | --- | --- | --- |
| 01 | [Rock vs Mine](projects/01-rock-vs-mine) | Binary classification | Logistic Regression | Test accuracy 76.2% | Bundled |
| 02 | [Diabetes Prediction](projects/02-diabetes-prediction) | Binary classification | Support Vector Classifier | Test accuracy 77.3% | Bundled |
| 03 | [House Price Prediction](projects/03-house-price-prediction) | Regression | XGBoost Regressor | Test R² 0.912 | In-notebook |
| 04 | [Fake News Prediction](projects/04-fake-news-prediction) | Text classification | TF-IDF + Logistic Regression | Test accuracy 97.9% | Add `data/train.csv` |
| 05 | [Loan Status Prediction](projects/05-loan-status-prediction) | Binary classification | Support Vector Classifier | Test accuracy 83.3% | Bundled |
| 06 | [Wine Quality Prediction](projects/06-wine-quality-prediction) | Classification | Random Forest | Accuracy 92.5% | Bundled |
| 07 | [Car Price Prediction](projects/07-car-price-prediction) | Regression | Linear Regression and Lasso | Test R² about 0.84–0.87 | Bundled |
| 08 | [Gold Price Prediction](projects/08-gold-price-prediction) | Regression | Random Forest Regressor | Reported R² 0.989 | Bundled |
| 09 | [Credit Card Fraud Detection](projects/09-credit-card-fraud-detection) | Imbalanced classification | Logistic Regression, under-sampled | Test accuracy 93.9% | Add `data/credit_data.csv` |
| 10 | [Heart Disease Prediction](projects/10-heart-disease-prediction) | Binary classification | Logistic Regression | Test accuracy 82.0% | Bundled |
| 11 | [Medical Insurance Cost](projects/11-medical-insurance-cost) | Regression | Linear Regression | Test R² 0.745 | Bundled |
| 12 | [Big Mart Sales](projects/12-bigmart-sales) | Regression | XGBoost Regressor | Test R² 0.587 | Bundled |
| 13 | [Customer Segmentation](projects/13-customer-segmentation) | Clustering | K-Means, k = 5 | Elbow method | Bundled |
| 14 | [Parkinson's Detection](projects/14-parkinsons-detection) | Binary classification | SVC + StandardScaler | Test accuracy 87.2% | Add `data/parkinsons.csv` |
| 15 | [Titanic Survival](projects/15-titanic-survival) | Binary classification | Logistic Regression | Test accuracy 78.2% | Bundled |
| 16 | [Calories Burnt](projects/16-calories-burnt) | Regression | XGBoost Regressor | See notebook | Add both CSVs |
| 17 | [Spam Mail Prediction](projects/17-spam-mail) | Text classification | TF-IDF + Logistic Regression | Test accuracy 96.6% | Bundled |
| 18 | [Movie Recommendation](projects/18-movie-recommendation) | Content-based retrieval | TF-IDF + cosine similarity | Similarity ranking | Bundled |
| 19 | [Breast Cancer Classification](projects/19-breast-cancer-classification) | Binary classification | Logistic Regression | Test accuracy 93.0% | Bundled via scikit-learn |

## Repository layout

```text
NIELIT-MACHINE-LEARNING-PROJECTS/
├── LICENSE
├── README.md
├── requirements.txt
└── projects/
    ├── 01-rock-vs-mine/
    │   ├── README.md
    │   ├── Project_1_Rock_vs_Mine_Prediction.ipynb
    │   └── data/
    ├── 02-diabetes-prediction/
    └── ...
```

Each project folder contains:

- the original notebook, with Colab paths rewritten to `data/...`
- a short README stating the task, model, and data requirement
- a `data/` directory when the table is small enough to keep in Git

## Quick start

```bash
git clone https://github.com/Rishabh-bgp/NIELIT-MACHINE-LEARNING-PROJECTS.git
cd NIELIT-MACHINE-LEARNING-PROJECTS
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

Open any notebook under `projects/`. Run the cells from the top. Paths are relative to the notebook directory.

## What each notebook does

The shared pipeline is deliberate and consistent:

1. Load the table and inspect shape, types, and missing values.
2. Explore distributions and, where useful, correlation.
3. Encode categorical fields and scale numeric fields when the model requires it.
4. Hold out a test split.
5. Fit one classical model and report accuracy or R² on train and test data.

Text projects add TF-IDF before the classifier. The movie project stops at cosine similarity and returns nearest titles. Customer segmentation uses the elbow method and does not use a supervised metric.

## Datasets that are not in the repository

Four notebooks expect files that were not part of the original upload. Drop them in the project `data/` folder under the name below, then run the notebook.

| Project | Expected file | Why it is absent |
| --- | --- | --- |
| Fake News | `projects/04-fake-news-prediction/data/train.csv` | External news corpus |
| Credit Card Fraud | `projects/09-credit-card-fraud-detection/data/credit_data.csv` | Large transaction file |
| Parkinson's Detection | `projects/14-parkinsons-detection/data/parkinsons.csv` | Not included in the original upload |
| Calories Burnt | `data/calories.csv` and `data/exercise.csv` | Not included in the original upload |

House price prediction loads data inside the notebook. `sklearn.datasets.load_boston()` was removed in scikit-learn 1.2. If that cell fails, replace it with:

```python
from sklearn.datasets import fetch_openml
boston = fetch_openml(name="boston", version=1, as_frame=True, parser="auto")
```

Breast cancer classification already uses `sklearn.datasets.load_breast_cancer()`. A copy of the Wisconsin diagnostic CSV is kept at `projects/19-breast-cancer-classification/data/wisconsin_breast_cancer.csv`. It was previously stored at the repository root under the ambiguous name `data.csv`.

## Stack

- Python 3.10 or newer
- pandas and NumPy for tabular work
- Matplotlib and Seaborn for exploratory plots
- scikit-learn for logistic regression, support vector machines, random forests, Lasso, TF-IDF, and K-Means
- XGBoost for the sales, house-price, and calories models
- Jupyter for the notebooks

Pinned ranges live in [`requirements.txt`](requirements.txt).

## Author

**Er. Rishabh Aryan**
M.Tech, Artificial Intelligence and Data Science
Indian Institute of Information Technology, Bhagalpur

- GitHub: [@Rishabh-bgp](https://github.com/Rishabh-bgp)
- ORCID: [0009-0004-7595-9440](https://orcid.org/0009-0004-7595-9440)

These notebooks are a personal practice collection from machine learning coursework. Public datasets remain the property of their original publishers.

## License

Released under the [MIT License](LICENSE).
