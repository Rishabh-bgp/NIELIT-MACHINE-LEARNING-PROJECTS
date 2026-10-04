# Contributing to NIELIT Machine Learning Projects

Thank you for considering a contribution. This repository is a public teaching collection of classical machine learning notebooks. Contributions are welcome when they make a notebook easier to run, easier to understand, or more honest about its result.

The maintainer is [Er. Rishabh Aryan](https://github.com/Rishabh-bgp). The project is released under the [MIT License](LICENSE). By submitting a pull request, you agree that your contribution may be distributed under that license.

Read this document before opening an issue or a pull request. Also read the [Code of Conduct](CODE_OF_CONDUCT.md) and, if you are reporting a vulnerability, [Security](SECURITY.md).

## Contents

- [Ways to contribute](#ways-to-contribute)
- [What we will not accept](#what-we-will-not-accept)
- [Before you start](#before-you-start)
- [Development setup](#development-setup)
- [Repository conventions](#repository-conventions)
- [Adding a project](#adding-a-project)
- [Changing an existing notebook](#changing-an-existing-notebook)
- [Datasets](#datasets)
- [Documentation](#documentation)
- [Commit messages](#commit-messages)
- [Pull requests](#pull-requests)
- [Issues](#issues)
- [Review process](#review-process)
- [Recognition](#recognition)

## Ways to contribute

Useful contributions include:

- A corrected data path, import, or cell that fails on a current Python install.
- A short explanation of a preprocessing choice that the notebook currently leaves implicit.
- A missing dataset note, or a documented pointer to a file that cannot be committed.
- A fix for a factual error in a project README or the root README.
- A new project that follows the folder layout below and does not duplicate an existing one.
- Clearer plots, axis labels, or metric reporting, provided the original result is not silently replaced.
- Typo and grammar fixes in Markdown.

Small, focused changes are preferred. A pull request that rewrites every notebook at once is difficult to review and will usually be asked to split.

## What we will not accept

- Notebooks that only call an API and do not show the data, the split, and the metric.
- Pickled models, virtual environments, checkpoints, or operating-system metadata.
- Datasets that you do not have the right to redistribute. When in doubt, do not commit the file. Document the source and the expected local path instead.
- Secrets, tokens, personal email exports, or private student records.
- Claims of clinical, financial, or legal readiness. These notebooks are educational.
- Changes that overwrite a saved score without saying that the number came from a new run.
- Automated formatting that touches every notebook without a functional reason.

## Before you start

1. Search [open issues](https://github.com/Rishabh-bgp/NIELIT-MACHINE-LEARNING-PROJECTS/issues) and pull requests so the same fix is not already in progress.
2. For a new project or a large rewrite, open an issue first and wait for a response. Use the Information Systems label when the change concerns the subject area of the repository.
3. For a typo, a broken path, or a one-cell bug, a pull request is enough.

## Development setup

Python 3.10 or newer is required.

```bash
git clone https://github.com/Rishabh-bgp/NIELIT-MACHINE-LEARNING-PROJECTS.git
cd NIELIT-MACHINE-LEARNING-PROJECTS
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

On Windows, activate with `.venv\Scripts\activate`.

Run a notebook from the repository root in Jupyter, or execute it from the command line:

```bash
jupyter nbconvert --to notebook --execute \
  projects/02-diabetes-prediction/Project_2_Diabetes_Prediction.ipynb \
  --output /tmp/executed.ipynb
```

Do not commit the executed copy. The path above writes it outside the repository on purpose.

If you add a library, add the lowest version you actually tested to `requirements.txt`, and name that version in the pull request.

## Repository conventions

The root holds the license, the catalog README, dependency bounds, and community documents. Project work lives under `projects/`.

```text
projects/NN-short-name/
├── README.md
├── Project_N_Descriptive_Name.ipynb
└── data/
    └── table.csv
```

- Number new projects sequentially. The current last number is 19.
- Use a lowercase slug with hyphens: `20-customer-churn`.
- Keep the notebook filename readable. Spaces are avoided in new names.
- Paths inside a notebook are relative to that notebook: `data/table.csv`, never `/content/...` and never an absolute machine path.
- One project, one primary notebook. Extra tables that the notebook does not train on must be named in the project README.
- Do not commit `.ipynb_checkpoints/`, `__MACOSX/`, `.DS_Store`, or `__pycache__/`.

## Adding a project

A new project is accepted when it teaches a distinct task or a distinct method. A second logistic-regression notebook on a near-copy of an existing table will be declined unless the write-up explains a new point.

Include all of the following:

1. A folder `projects/NN-short-name/`.
2. The notebook, runnable from a clean environment after `pip install -r requirements.txt`.
3. A project README with the task, the target column, the model, the split, the data file, and any known limit.
4. The dataset, if it is small and redistributable. Otherwise a `data/.gitkeep` and the exact filename the notebook expects.
5. A row in the catalog table in the root README, plus a project note and a dataset-inventory row if a file is bundled.
6. Cleared notebook outputs are acceptable. If you leave outputs, they must come from the run you describe. Do not paste another person's score.

Suggested notebook order:

1. State the question in a Markdown cell.
2. Import dependencies.
3. Load and inspect the table, including missing values.
4. Separate features and target.
5. Encode or scale only what the model requires, and say why.
6. Split with an explicit `test_size` and `random_state`. Stratify classification labels.
7. Fit the model.
8. Report training and test metrics. For classification, accuracy alone is not enough on an imbalanced label. Add precision, recall, or a confusion matrix.
9. State one limitation.

## Changing an existing notebook

These notebooks already have saved scores. A contribution may improve the code, but it must not pretend the old number still applies.

- If you change a path only, keep the cells and the stored outputs.
- If you change the split, the features, or the model, clear the old outputs and write the new score in the project README and the root catalog. Mark it as a new run, with the date and the library versions.
- Do not rename a project folder unless every link in the root README is updated in the same pull request.
- Do not delete a project to replace it. Add the replacement beside it, or discuss the removal in an issue first.

House price prediction still calls `sklearn.datasets.load_boston()`. A pull request that switches it to `fetch_openml` is welcome if the README states that the target definition may differ from the saved R².

## Datasets

Commit a table only when all of these are true:

- You have the right to redistribute it.
- The file is the one the notebook reads.
- The uncompressed file is comfortably under GitHub's 50 MB recommended limit. The movie table is already large; do not add another file of that size without discussing it first.
- The header and the label column are documented.

Do not commit zip archives if the CSV is the file users need, except when the uncompressed file is too large. Do not commit macOS resource forks.

For a file that cannot be committed, document:

- the expected relative path
- the column the notebook treats as the target
- a public source, without implying that this repository redistributes that source

Personal data, even if anonymised casually, does not belong here.

## Documentation

The root README is the catalog. Keep it accurate.

- Every new project gets a catalog row, a project note, and a layout that matches the real folder.
- Scores are described as saved notebook results unless you re-ran them and say so.
- Subject label for this repository is Information Systems. Use that label on issues that concern the collection as a whole.
- English is the language of the README, issue templates, and commit messages. Notebook comments may stay as they are unless you are already editing that cell.

## Commit messages

Use a short imperative subject, then a blank line, then the reason.

```text
Point the heart-disease notebook at data/heart.csv

The Colab path failed outside Google Colab, and the old data.csv name belonged to the breast-cancer table.
```

One concern per commit when you can. Do not commit data files and unrelated prose in a way that hides the data change.

## Pull requests

1. Fork the repository and create a branch from `main`. Branch names such as `fix/loan-path` or `project/20-churn` are easier to review than `update`.
2. Make the change and run the notebook you touched.
3. Open the pull request against `main`. Fill in the template.
4. Link the related issue if one exists.
5. Expect a review. A maintainer may ask for a smaller diff or a README update.

A complete pull request states:

- what changed
- why it changed
- how you checked it
- whether any saved score is now stale
- whether a new dataset is included, and on what terms

Draft pull requests are appropriate for work you want seen before it is ready.

## Issues

Use the templates in `.github/ISSUE_TEMPLATE` when they fit.

- Bug: a notebook, path, or documented command fails.
- New project: propose the task, the data source, and the model before writing the notebook.
- Dataset: a bundled file is wrong, or a missing file needs a documented source.
- Documentation: the README disagrees with the notebook.

Include the project folder, the cell or file, the Python version, and the error text. A screenshot of a traceback is not a substitute for the traceback.

Security reports do not belong in a public issue. See [SECURITY.md](SECURITY.md).

## Review process

The maintainer reviews pull requests when able. There is no guaranteed response time. A change may be accepted, accepted with edits, or closed with an explanation.

Maintainers may commit small follow-up fixes to a contribution branch when that option is left enabled. Those edits stay under the same license.

This is a personal academic collection. Silence on an issue is not approval to merge a large rewrite.

## Recognition

Contributors are credited by their GitHub account on the merged commit. Substantial notebook contributions may be named in the project README. Do not add yourself to the author block of the root README; that block identifies the collection's author.
