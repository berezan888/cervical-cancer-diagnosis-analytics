
# Cervical Cancer Risk Prediction Using Machine Learning

**Bachelor's Thesis | Data Science & Machine Learning**  
**Author:** Anna Berezan  
**Academic Year:** 2025/2026

---

## Project Overview

This project explores the application of machine learning techniques to cervical cancer risk prediction. The main objective is to evaluate and compare different classification algorithms, investigate the impact of diagnostic attributes on model performance, and identify important risk factors using explainable AI techniques.

Four classification algorithms were implemented and evaluated:

- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)
- XGBoost

The project focuses on two main aspects:

1. **Predictive performance:** Evaluating how accurately machine learning models can identify cervical cancer cases using different feature sets.
2. **Model interpretability:** Understanding which features contribute most to model predictions using SHAP (SHapley Additive exPlanations).

An additional experiment was conducted using a second dataset containing behavioral and psychosocial risk factors to investigate model performance on a smaller dataset with a different set of features.

## Key Features

- Exploratory Data Analysis (EDA) and data visualization
- Data cleaning and preprocessing
- Handling missing values using KNN Imputation
- Feature scaling using StandardScaler
- Handling class imbalance using SMOTE
- Implementation of four classification algorithms
- Hyperparameter optimization using GridSearchCV
- 5-fold cross-validation
- Model evaluation and performance comparison
- Ablation study to investigate the impact of diagnostic features
- Model interpretability using SHAP
- Feature importance and risk factor analysis

## Project Structure

```text
├── 01_Exploratory_Data_Analysis.ipynb
├── 02_Baseline_Model_Benchmarking.ipynb
├── 03_Model_Optimization_and_Ablation_Study.ipynb
├── 04_New_Dataset_Experiment.ipynb
├── risk_factors_cervical_cancer.csv
├── sobar-72.csv
└── README.md
```

## Methodology

The project is organized into four main stages.

### 01 — Exploratory Data Analysis (EDA)

Dataset: Cervical Cancer Risk Factors

- 858 patient records
- 36 attributes

The first stage focuses on understanding the dataset, identifying data quality issues, and exploring relationships between features and the target variable (`Biopsy`).

Key activities:

- Data cleaning and preprocessing
- Replacing missing value indicators (`?`) with `NaN`
- Data type conversion
- Feature classification into binary (24) and numerical (12) attributes
- Missing value analysis
- Feature distribution analysis
- Exploration of relationships between individual features and the target variable
- Data visualization

### 02 — Baseline Model Benchmarking

The second stage establishes baseline performance for four classification algorithms without hyperparameter optimization.

Models evaluated:

- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)
- XGBoost

Experimental setup:

- Train-test split: 80/20
- Model training using the original feature set
- Comparison of classification performance

Evaluation metrics:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

Confusion matrices were also generated to analyze classification errors and compare model performance.

### 03 — Model Optimization and Ablation Study

This stage represents the main experimental part of the project.

The objective is to improve model performance, evaluate the contribution of diagnostic features, and understand the factors influencing predictions.

**Data preprocessing:**

- KNN Imputer for missing value handling
- StandardScaler for feature normalization
- SMOTE for handling class imbalance
- SMOTE applied exclusively to training data to prevent data leakage

**Model optimization:**

- Hyperparameter tuning using GridSearchCV
- 5-fold cross-validation
- Recall-based optimization (`scoring='recall'`)

**Ablation study:**

Two feature configurations were compared:

1. Full dataset — including all available attributes.
2. Reduced dataset — excluding diagnostic test attributes.

This experiment investigates how model performance changes when diagnostic information is removed.

**Model interpretability:**

SHAP was used to:

- Identify the most influential features
- Analyze feature contributions to model predictions
- Improve model transparency
- Investigate potentially important risk factors

**Composite model selection score:**

A weighted scoring system was used to select the best-performing model:

- Recall: 40%
- ROC-AUC: 35%
- F1-score: 25%

This approach prioritizes the identification of positive cases while maintaining a balance between overall classification performance and precision-recall trade-offs.

### 04 — Experiment on a New Dataset

Dataset: Cervical Cancer Behavior Risk

- 72 patient records
- 19 attributes

The final stage evaluates the models on a second dataset focused on behavioral and psychosocial risk factors.

Key activities:

- Exploratory analysis of behavioral and psychosocial attributes
- Data preprocessing
- Model evaluation with and without SMOTE
- 5-fold cross-validation
- Comparison of classification performance
- SHAP-based interpretation of the best-performing model

This experiment provides an additional perspective on cervical cancer risk prediction using a different set of features and a smaller dataset.

## Datasets

Two datasets from the UCI Machine Learning Repository were used.

| Dataset | Source | Records | Features | Target Variable |
|---|---|---:|---:|---|
| Cervical Cancer Risk Factors | UCI ML Repository | 858 | 36 | `Biopsy` |
| Cervical Cancer Behavior Risk | UCI ML Repository | 72 | 19 | `ca_cervix` |

Both datasets are available through the [UCI Machine Learning Repository](https://archive.ics.uci.edu/).

## Technologies & Tools

**Programming Language:**
- Python 3.10+

**Data Analysis & Visualization:**
- Pandas
- NumPy
- Matplotlib
- Seaborn

**Machine Learning:**
- Scikit-learn
- XGBoost
- Imbalanced-learn

**Explainable AI:**
- SHAP

**Development Environment:**
- Jupyter Notebook

## Installation

### Requirements

- Python 3.10 or higher
- pip

### Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn shap jupyter
```

## Running the Project

1. Clone or download the repository:

```bash
git clone <repository-url>
```

2. Navigate to the project directory:

```bash
cd <project-directory>
```

3. Install the required dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn shap jupyter
```

4. Make sure both datasets are located in the same directory as the notebooks.

5. Launch Jupyter Notebook:

```bash
jupyter notebook
```

6. Run the notebooks in the following order:

```text
01_Exploratory_Data_Analysis.ipynb
02_Baseline_Model_Benchmarking.ipynb
03_Model_Optimization_and_Ablation_Study.ipynb
04_New_Dataset_Experiment.ipynb
```

## Key Results

The experiments demonstrated the importance of diagnostic attributes for cervical cancer classification.

**Full Dataset:**

- Best-performing model: Random Forest
- Accuracy: 0.971
- ROC-AUC: 0.940
- Recall: up to 0.818 across the evaluated models

**Reduced Dataset (without diagnostic attributes):**

- Best-performing model: XGBoost
- Recall: 0.455
- ROC-AUC: 0.692
- Recall across evaluated models: 0.273–0.455

**Main Findings:**

- Removing diagnostic attributes resulted in a noticeable decrease in predictive performance.
- Diagnostic features contributed significantly to the models' ability to identify positive cases.
- Random Forest achieved the best overall performance on the full dataset.
- XGBoost performed best on the reduced feature set according to the selected evaluation criteria.
- SHAP analysis provided insights into the features influencing model predictions and helped identify potentially important risk factors across both datasets.

## Important Considerations

This project is an academic machine learning study and is not intended for clinical use.

The datasets are relatively small, and the experimental results should be interpreted with consideration of their size, class imbalance, and feature availability.

The models are intended for research and educational purposes only and should not be considered a substitute for professional medical diagnosis.

## Author

**Anna Berezan**

Bachelor's Thesis — Data Science & Machine Learning  
Academic Year: 2025/2026

---

**Project Version:** 1.0.0
