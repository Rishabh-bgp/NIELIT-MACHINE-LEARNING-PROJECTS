# NIELIT Machine Learning Projects

A catalog of nineteen classical machine learning projects, prepared as runnable Jupyter notebooks. The collection covers binary classification, text classification, regression, clustering, and content-based recommendation. Every bundled project can be opened from a fresh clone: the dataset sits next to the notebook, and the old Google Colab paths have been rewritten to local `data/` files.

This repository is a practice record, not a production model registry. Scores printed below are the values already saved in the notebook outputs. They describe that run, with that split and that preprocessing. Re-run a notebook before treating a number as current.

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-classical%20ML-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-gradient%20boosting-1A7F37)](https://xgboost.readthedocs.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg)](LICENSE)

## Contents

- [What this repository contains](#what-this-repository-contains)
- [Catalog](#catalog)
- [Repository layout](#repository-layout)
- [Setup](#setup)
- [How a notebook is organized](#how-a-notebook-is-organized)
- [Project notes](#project-notes)
- [Dataset inventory](#dataset-inventory)
- [Files that are not bundled](#files-that-are-not-bundled)
- [Reproducibility](#reproducibility)
- [Stack](#stack)
- [Author](#author)
- [License](#license)

## What this repository contains

The original upload placed every notebook and every zip archive in the repository root. The README was a title only, several filenames contained spaces, and each notebook loaded data from `/content/...`, which exists only inside Colab. One file named `data.csv` was in fact the Wisconsin breast-cancer table, while the heart-disease notebook expected a file of that name.

The current layout fixes that:

- Each notebook has its own directory under `projects/`.
- Each directory has a short README and a `data/` folder.
- Zip archives were unpacked. macOS metadata (`__MACOSX`) was not committed.
- Colab absolute paths were replaced with paths relative to the notebook, such as `data/train.csv`.
- Heart disease now reads `data/heart.csv`. The breast-cancer CSV is stored under its real name.
- `requirements.txt` lists the libraries the notebooks import.

Original notebook filenames are unchanged, so an old link of the form `Project_10_Heart_Disease_Prediction.ipynb` can still be found by name inside its project folder.

## Catalog

| # | Project | Task | Model | Split | Reported result | Data |
| --- | --- | --- | --- | --- | --- | --- |
| 01 | [Rock vs Mine](projects/01-rock-vs-mine) | Binary classification | Logistic Regression | 10% test, stratified, `random_state=1` | Test accuracy 76.2% | Bundled |
| 02 | [Diabetes Prediction](projects/02-diabetes-prediction) | Binary classification | SVC, scaled features | 20% test, stratified, `random_state=2` | Test accuracy 77.3% | Bundled |
| 03 | [House Price Prediction](projects/03-house-price-prediction) | Regression | XGBoost Regressor | 20% test, `random_state=2` | Test R² 0.912 | In-notebook |
| 04 | [Fake News Prediction](projects/04-fake-news-prediction) | Text classification | TF-IDF + Logistic Regression | 20% test, stratified, `random_state=2` | Test accuracy 97.9% | Add file |
| 05 | [Loan Status Prediction](projects/05-loan-status-prediction) | Binary classification | SVC | 10% test, stratified, `random_state=2` | Test accuracy 83.3% | Bundled |
| 06 | [Wine Quality Prediction](projects/06-wine-quality-prediction) | Classification | Random Forest | 20% test, `random_state=3` | Accuracy 92.5% | Bundled |
| 07 | [Car Price Prediction](projects/07-car-price-prediction) | Regression | Linear Regression and Lasso | 10% test, `random_state=2` | Test R² about 0.84–0.87 | Bundled |
| 08 | [Gold Price Prediction](projects/08-gold-price-prediction) | Regression | Random Forest Regressor | 20% test, `random_state=2` | Reported R² 0.989 | Bundled |
| 09 | [Credit Card Fraud Detection](projects/09-credit-card-fraud-detection) | Imbalanced classification | Logistic Regression after under-sampling | 20% test, stratified, `random_state=2` | Test accuracy 93.9% | Add file |
| 10 | [Heart Disease Prediction](projects/10-heart-disease-prediction) | Binary classification | Logistic Regression | 20% test, stratified, `random_state=2` | Test accuracy 82.0% | Bundled |
| 11 | [Medical Insurance Cost](projects/11-medical-insurance-cost) | Regression | Linear Regression | 20% test, `random_state=2` | Test R² 0.745 | Bundled |
| 12 | [Big Mart Sales](projects/12-bigmart-sales) | Regression | XGBoost Regressor | 20% test, `random_state=2` | Test R² 0.587 | Bundled |
| 13 | [Customer Segmentation](projects/13-customer-segmentation) | Clustering | K-Means, k = 5 | Unsupervised | Elbow method | Bundled |
| 14 | [Parkinson's Detection](projects/14-parkinsons-detection) | Binary classification | SVC + StandardScaler | 20% test, `random_state=2` | Test accuracy 87.2% | Add file |
| 15 | [Titanic Survival](projects/15-titanic-survival) | Binary classification | Logistic Regression | See notebook | Test accuracy 78.2% | Bundled |
| 16 | [Calories Burnt](projects/16-calories-burnt) | Regression | XGBoost Regressor | See notebook | See notebook | Add files |
| 17 | [Spam Mail Prediction](projects/17-spam-mail) | Text classification | TF-IDF + Logistic Regression | See notebook | Test accuracy 96.6% | Bundled |
| 18 | [Movie Recommendation](projects/18-movie-recommendation) | Content-based retrieval | TF-IDF + cosine similarity | No supervised split | Nearest-title ranking | Bundled |
| 19 | [Breast Cancer Classification](projects/19-breast-cancer-classification) | Binary classification | Logistic Regression | See notebook | Test accuracy 93.0% | Bundled via scikit-learn |

Accuracy on a balanced or under-sampled set is not the same as precision or recall on the original class distribution. The fraud notebook in particular reports accuracy after under-sampling. Read that result as a training-procedure score, not as a production false-positive rate.

## Repository layout

```text
NIELIT-MACHINE-LEARNING-PROJECTS/
├── LICENSE
├── README.md
├── requirements.txt
├── .gitignore
└── projects/
    ├── 01-rock-vs-mine/
    │   ├── README.md
    │   ├── Project_1_Rock_vs_Mine_Prediction.ipynb
    │   └── data/
    │       └── sonar.csv
    ├── 02-diabetes-prediction/
    └── ...
```

A project folder always contains the notebook and a README. It contains CSV files only when those files were in the original upload. Projects that still need an external file keep an empty `data/` directory and a `.gitkeep`, so the expected path already exists.

## Setup

Python 3.10 or newer is assumed.

```bash
git clone https://github.com/Rishabh-bgp/NIELIT-MACHINE-LEARNING-PROJECTS.git
cd NIELIT-MACHINE-LEARNING-PROJECTS
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

On Windows, activate the environment with `.venv\Scripts\activate`.

Open a notebook from its project directory, or start Jupyter at the repository root and navigate into `projects/`. Paths inside the notebooks are relative to the notebook file, not to the shell's current directory. Jupyter resolves them from the notebook's folder, which is the intended way to run these files.

To run one project without the browser:

```bash
jupyter nbconvert --to notebook --execute \
  projects/02-diabetes-prediction/Project_2_Diabetes_Prediction.ipynb \
  --output executed.ipynb
```

Execution will fail for the four projects whose datasets are not bundled, and for house-price prediction on scikit-learn 1.2 or newer, until the data cell is updated. Those cases are listed below.

## How a notebook is organized

The notebooks follow one teaching pipeline, with small variations.

1. Import NumPy, pandas, and the model class.
2. Load the table and print shape, head, and missing-value counts.
3. Separate features `X` from the target `Y`.
4. Encode categorical columns where the model cannot take strings. Loan, insurance, car price, Big Mart, and Titanic do this.
5. Scale numeric features when the model is distance-based or margin-based. Diabetes and Parkinson's use `StandardScaler`.
6. Hold out a test split. Most classification notebooks stratify on the label and set a fixed `random_state`.
7. Fit one model. There is no grid search and no cross-validation in the saved notebooks.
8. Print training and test accuracy, or R² and mean absolute error for regression.
9. In several notebooks, run one hand-written example through `predict`.

Text projects insert a TF-IDF step before logistic regression. The movie project stops after cosine similarity and returns neighbouring titles. Customer segmentation has no label: it plots within-cluster sum of squares and fits K-Means with five clusters.

## Project notes

### 01. Rock vs Mine

Sonar returns are classified as rock (`R`) or mine (`M`) from 60 frequency-band measurements. The table has no header row. Logistic regression is trained on a 90/10 stratified split. The saved test accuracy is 76.2%, against 83.4% on the training split. The gap is expected on a small sonar set. File: `projects/01-rock-vs-mine/data/sonar.csv`.

### 02. Diabetes Prediction

The Pima Indians diabetes table supplies pregnancies, glucose, blood pressure, skin thickness, insulin, BMI, diabetes pedigree function, and age. The target is the binary `Outcome` column. Features are standardized, then a support vector classifier is fit on an 80/20 stratified split. Saved test accuracy is 77.3%. File: `data/diabetes.csv`.

### 03. House Price Prediction

XGBoost regresses median house value. The notebook loads the Boston housing set with `sklearn.datasets.load_boston()`, which was removed in scikit-learn 1.2. On a current install, replace that cell with:

```python
from sklearn.datasets import fetch_openml
boston = fetch_openml(name="boston", version=1, as_frame=True, parser="auto")
```

The saved notebook reports test R² of 0.912 and test mean absolute error of about 1.99, in the units of the Boston target. No CSV is bundled.

### 04. Fake News Prediction

Article text is vectorized with TF-IDF and classified with logistic regression on a 20% stratified hold-out. The saved test accuracy is 97.9%. That figure belongs to the file the notebook was originally run against. Place that file at `projects/04-fake-news-prediction/data/train.csv` before executing. The notebook now points at that relative path.

### 05. Loan Status Prediction

Loan approval is predicted from gender, marital status, dependents, education, self-employment, applicant and coapplicant income, loan amount, term, credit history, and property area. Missing values are filled and categorical fields are encoded. An SVC is evaluated on a 10% stratified split. Saved test accuracy is 83.3%, which is higher than the training accuracy of 79.9% because the test slice is small. File: `data/loan.csv`, renamed from `Loan dataset.csv`. The notebook used to request `/content/dataset.csv`.

### 06. Wine Quality Prediction

Red-wine quality is predicted from eleven physicochemical measurements: fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free and total sulfur dioxide, density, pH, sulphates, and alcohol. A random forest is trained after a correlation plot. The notebook records an accuracy of 92.5%. The quality label is ordinal; the notebook treats the task as classification rather than ordered regression. File: `data/winequality-red.csv`.

### 07. Car Price Prediction

Selling price is estimated from year, present price, kilometres driven, fuel type, seller type, transmission, and owner count. Categorical fields are encoded. Linear regression and Lasso are both fit on a 10% hold-out. Saved test R² values fall around 0.84 to 0.87. The notebook reads `data/car_data.csv`. Three additional CarDekho extracts are kept in the same `data/` folder for inspection; they are not the file the notebook trains on.

### 08. Gold Price Prediction

The target is the GLD price. Predictors are SPX, USO, SLV, and EUR/USD. Date is not used as a feature. A random forest regressor is fit after a correlation check; silver is strongly associated with GLD in the saved output. The notebook records an R² of 0.989. File: `data/gld_price_data.csv`. The original Colab path was `/content/gold price dataset.csv`.

### 09. Credit Card Fraud Detection

The notebook states that the transaction table is highly unbalanced, with a small fraudulent class, and then under-samples the legitimate class before logistic regression. Saved test accuracy after that procedure is 93.9%. Accuracy after balancing is not a substitute for precision, recall, or precision-recall area on the original distribution. The CSV is not in the repository because the public transaction file is large. Place it at `projects/09-credit-card-fraud-detection/data/credit_data.csv`.

### 10. Heart Disease Prediction

Presence of heart disease is predicted from age, sex, chest-pain type, resting blood pressure, cholesterol, fasting blood sugar, resting ECG, maximum heart rate, exercise-induced angina, oldpeak, slope, number of major vessels, and thalassemia status. The label is binary: `1` for a defective heart and `0` for a healthy heart, as coded in the notebook. Logistic regression on a 20% stratified split reports 82.0% test accuracy and 85.1% training accuracy. File: `data/heart.csv`. This is the file formerly named `heart_disease_data.csv`, not the root `data.csv` from the original upload.

### 11. Medical Insurance Cost

Charges are regressed on age, sex, BMI, number of children, smoker status, and region. Sex, smoker, and region are encoded. Linear regression on a 20% hold-out reports a test R² of 0.745, close to the training R² of 0.752. One saved prediction example returns a charge of about 3,760 USD. File: `data/insurance.csv`.

### 12. Big Mart Sales

Item outlet sales are forecast from item weight, fat content, visibility, type, MRP, and outlet identifier, establishment year, size, location type, and outlet type. Label encoding prepares the categorical columns for XGBoost. The saved test R² is 0.587, against 0.636 on the training split. `data/Train.csv` is the training table. `data/Test.csv` is included and has no sales target.

### 13. Customer Segmentation

Mall customers are grouped by annual income and spending score. Gender and age are inspected, but the clustering plot uses the two spending features. Within-cluster sum of squares is computed for a range of `k`, and the notebook selects five clusters. There is no accuracy score; the result is a partition, not a prediction. File: `data/Mall_Customers.csv`.

### 14. Parkinson's Disease Detection

Biomedical voice measurements are standardized and passed to a support vector classifier. The saved test accuracy is 87.2%, against 88.5% on the training split. The CSV was not in the original upload. Place it at `projects/14-parkinsons-detection/data/parkinsons.csv`. The notebook already points at that path.

### 15. Titanic Survival

Survival is predicted from passenger class, sex, age, siblings and spouses aboard, parents and children aboard, and fare. Cabin is sparse and is not the main signal in this pipeline. Missing age and embarked values are handled before logistic regression. Saved test accuracy is 78.2%, against 80.8% on the training split. `data/train.csv` is the file the notebook reads. `data/test.csv` and `data/gender_submission.csv` are the companion Kaggle files and are not required for the training cells.

### 16. Calories Burnt

Exercise records and calorie records are joined, then an XGBoost regressor predicts calories from duration, heart rate, age, and body measurements. Both source files were absent from the upload. Place `calories.csv` and `exercise.csv` in `projects/16-calories-burnt/data/` before running.

### 17. Spam Mail Prediction

Messages are labelled ham or spam. Text is converted with TF-IDF and classified with logistic regression. Saved test accuracy is 96.6%, nearly identical to the training accuracy of 96.7%. File: `data/mail_data.csv`, with columns `Category` and `Message`.

### 18. Movie Recommendation

This is the only retrieval project. Movie text metadata is vectorized with TF-IDF, and recommendations are the titles with the highest cosine similarity to a query title. There is no train/test score. `data/movies.csv` is about 23 MB uncompressed, which is why this folder dominates the clone size. The original archive was `movies.csv.zip`.

### 19. Breast Cancer Classification

Tumours are classified as malignant or benign with logistic regression on the Wisconsin diagnostic features: radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, and fractal dimension, each in mean, standard-error, and worst form. The notebook loads the table through `sklearn.datasets.load_breast_cancer()`, so it runs without a local CSV. Saved test accuracy is 93.0%, against 94.9% on the training split. A CSV copy is kept at `data/wisconsin_breast_cancer.csv` for inspection. That file was previously committed at the repository root as `data.csv`.

## Dataset inventory

| Project file | Rows of interest | Columns used by the notebook |
| --- | --- | --- |
| `01-rock-vs-mine/data/sonar.csv` | No header | 60 numeric bands, label `R` or `M` |
| `02-diabetes-prediction/data/diabetes.csv` | Outcome is the label | 8 clinical features |
| `05-loan-status-prediction/data/loan.csv` | `Loan_Status` | Applicant, loan, and property fields |
| `06-wine-quality-prediction/data/winequality-red.csv` | `quality` | 11 chemical measurements |
| `07-car-price-prediction/data/car_data.csv` | `Selling_Price` | Year, present price, kilometres, fuel, seller, transmission, owner |
| `08-gold-price-prediction/data/gld_price_data.csv` | `GLD` | SPX, USO, SLV, EUR/USD |
| `10-heart-disease-prediction/data/heart.csv` | `target` | 13 clinical features |
| `11-medical-insurance-cost/data/insurance.csv` | `charges` | age, sex, bmi, children, smoker, region |
| `12-bigmart-sales/data/Train.csv` | `Item_Outlet_Sales` | Item and outlet attributes |
| `13-customer-segmentation/data/Mall_Customers.csv` | No label | Annual income and spending score for clustering |
| `15-titanic-survival/data/train.csv` | `Survived` | Class, sex, age, family counts, fare |
| `17-spam-mail/data/mail_data.csv` | `Category` | `Message` |
| `18-movie-recommendation/data/movies.csv` | No supervised label | Text metadata for TF-IDF |
| `19-breast-cancer-classification/data/wisconsin_breast_cancer.csv` | `diagnosis` | 30 numeric morphology features |

Public tables remain the property of their original publishers. This repository only stores the copies required to rerun the notebooks.

## Files that are not bundled

| Project | Place this file here | Consequence if missing |
| --- | --- | --- |
| Fake News | `projects/04-fake-news-prediction/data/train.csv` | `read_csv` fails |
| Credit Card Fraud | `projects/09-credit-card-fraud-detection/data/credit_data.csv` | `read_csv` fails |
| Parkinson's Detection | `projects/14-parkinsons-detection/data/parkinsons.csv` | `read_csv` fails |
| Calories Burnt | `projects/16-calories-burnt/data/calories.csv` and `exercise.csv` | Both joins fail |
| House Price | None; loaded in code | `load_boston` fails on scikit-learn 1.2+ |

## Reproducibility

- Splits use a fixed `random_state` in almost every notebook, so a rerun on the same library versions should land close to the saved score.
- Library versions are not fully pinned. `requirements.txt` sets lower bounds only. A future scikit-learn or XGBoost release can move a score.
- There is no cross-validation. A single hold-out on a small table, especially the 10% loan and sonar splits, has a wide error bar.
- Preprocessing is fit on the whole frame in some notebooks before the split. That is acceptable for a teaching notebook and is not a claim of a leakage-free pipeline.
- Class imbalance is handled explicitly only in the fraud notebook, and only by under-sampling.
- No model is exported. Nothing in this repository is a saved `.pkl` or an inference service.

## Stack

| Library | Role in these notebooks |
| --- | --- |
| pandas | Loading, missing-value checks, encoding prep |
| NumPy | Arrays passed to `predict` |
| Matplotlib, Seaborn | Distributions, correlation, cluster elbow plot |
| scikit-learn | Logistic regression, SVC, random forest, Lasso, TF-IDF, K-Means, metrics, splits |
| XGBoost | House price, Big Mart sales, calories burnt |
| Jupyter | Notebook interface |

Install with `pip install -r requirements.txt`.

## Author

**Er. Rishabh Aryan**
M.Tech, Artificial Intelligence and Data Science
Department of Computer Science and Engineering
Indian Institute of Information Technology, Bhagalpur

- GitHub: [@Rishabh-bgp](https://github.com/Rishabh-bgp)
- ORCID: [0009-0004-7595-9440](https://orcid.org/0009-0004-7595-9440)

These notebooks are a personal practice collection from machine learning coursework.

## License

Released under the [MIT License](LICENSE).
