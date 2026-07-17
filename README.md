# ml-03-classification

[![Workflow Guide](https://img.shields.io/badge/Pro--Guide-pro--analytics--02-green)](https://denisecase.github.io/pro-analytics-02/workflow-b-apply-example-project/)
[![Python 3.14](https://img.shields.io/badge/python-3.14%2B-blue?logo=python)](./pyproject.toml)
[![MIT](https://img.shields.io/badge/license-see%20LICENSE-yellow.svg)](./LICENSE)

> Professional Python project: building and evaluating classification models.

Project Description
This project implements Module 3 classification workflows using a custom dataset instead of the built‑in Seaborn penguins dataset. The custom dataset (penguin_neighbor.csv) includes penguin measurements and a manually created categorical label called neighborhood, which becomes the target for prediction.

The project demonstrates:

loading and cleaning a custom CSV dataset

normalizing inconsistent categorical values

encoding categorical features

balancing classes for stratified splitting

training and evaluating a Decision Tree classifier

performing a parameter sweep (max_depth)

interpreting confusion matrices and classification reports

documenting results in a reproducible notebook

This project shows how to adapt the example workflow to a realistic, messy dataset and make analyst‑driven modeling decisions.

Assignment Notebooks
Main notebook used for this assignment:

notebooks/ml_03_rucu.ipynb (your custom notebook)

Supporting example notebook:

notebooks/ml_03_case.ipynb

Custom Dataset
Your custom dataset is located at:

Code
data/raw/penguin_neighbor.csv
It includes:

bill_length_mm

bill_depth_mm

species

island

neighborhood (custom target)

Key Data Challenges You Solved
inconsistent capitalization (north, NORTH, North)

trailing whitespace

encoding issues

class imbalance (some neighborhoods had only one row)

NA‑dropping reducing class counts

stratification errors

You fixed these by:

using .str.strip().str.title()

adding additional rows

re‑encoding categories

rebuilding df_model after cleaning

Modeling Approach
This is a supervised classification problem because the dataset includes a target (neighborhood) with discrete categories.

You used:

DecisionTreeClassifier

StandardScaler

train_test_split with stratify=y

max_depth sweep from 1 to 12

Why a Decision Tree?
interpretable

works well on small datasets

handles encoded categorical features

easy to tune

appropriate for your custom target

Custom Target: Neighborhood
The example project predicts species.
Your custom project predicts neighborhood, which required:

cleaning inconsistent labels

adding rows to balance classes

re‑encoding categories

This change matters because it transforms the project into a realistic ML workflow where data preparation is essential.

Features Used
You selected features available in your custom CSV:

bill_length_mm

bill_depth_mm

species (encoded)

island (encoded)

You removed features not present in your dataset (flipper length, body mass).

Evaluation and Results
You evaluated your model using:

accuracy score

classification report

confusion matrix

parameter sweep

Key Results
The model trained successfully after cleaning the dataset.

The confusion matrix showed correct predictions across all neighborhoods.

The parameter sweep revealed the classic pattern:

shallow trees underfit

deep trees overfit

max_depth=3 provided the best balance

Phase 4 Modification
You modified the example project by:

replacing the dataset

cleaning and encoding the custom target

balancing classes

updating the feature list

fixing stratification errors

Phase 5 Custom Project
You implemented a full custom classification workflow predicting neighborhood instead of species. This required adapting the example notebook to a new dataset, selecting appropriate features, cleaning the target, and tuning the model.

Commands Used
shell
uv self update
uv python pin 3.14
uv lock --upgrade
uv sync --extra dev --extra docs --upgrade

uvx pre-commit install
uvx pre-commit run --all-files

uv run python -m nbconvert --to notebook --execute --inplace notebooks/ml_03_rucu.ipynb

uv run ruff format .
uv run ruff check . --fix
uv run python -m pyright
uv run python -m pytest
Documentation
Your project narrative and results are located in:

Code
docs/index.md
License
MIT License — see LICENSE file.
