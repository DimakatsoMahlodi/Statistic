# STATISTIC
## Statistic Report

## Credit Card Default Analysis Report

### Abstract

This report presents the analytical workflow conducted on the Credit Card Default dataset, focusing on descriptive statistics, inferential analysis, predictive modelling, and introductory causal inference. The objective was to understand client repayment behaviour, identify significant predictors of default, and build reliable modelling pipelines for risk assessment. The dataset was examined for inconsistencies, class imbalance, and skewed features, followed by rigorous analytical procedures including hypothesis testing, model evaluation, threshold selection, and interpretability using SHAP values. The resulting outputs provide a comprehensive foundation for statistical understanding and predictive risk modelling.

### Repository Layout

#### This repository contains:

A single analysis notebook: Credit_Card_Default_Analysis___.ipynb

Raw dataset: default of credit card clients.csv

README documentation (this file)

The notebook integrates descriptive, inferential, predictive, and causal frameworks within one cohesive workflow.

#### Dataset

default of credit card clients.csv – Records of 30,000 credit card clients with multiple financial, demographic, and behavioural features relevant to credit risk assessment.

#### Key feature groups include:

Demographics: sex, age, education, marriage

Credit attributes: credit limit

Payment history: PAY_1 to PAY_6

Bill amounts: BILL_AMT1–6

Payment amounts: PAY_AMT1–6

Target variable: default_payment_next_month (0/1)

### ⚙️ Methodology

#### 1. Data Inspection

Loaded the dataset and confirmed 30,000 rows × 25 columns.

Verified all data types (numerical, categorical, ordinal).

Explored distribution shapes (e.g., heavy right tail in bill amounts).

Identified class imbalance: Default rate ≈ 22%.

### 2. Handling Missing Values

The dataset contains no NULL values, but logical inspection was conducted to ensure:

Consistency in demographic categories

Valid ranges for bill amounts and payment amounts

No impossible or undefined payment statuses

Minor formatting issues (categorical encodings) were standardized during preprocessing.

### 3. Duplicate Review

Dataset was checked for duplicate entries.

No exact duplicates were found across the 30,000 observations.

However, repeated behavioural patterns (e.g., same payment history) were retained as they represent real clients.

### 4. Outlier Detection and Treatment

The notebook examined outliers conceptually for:

Bill amounts

Payment amounts

Credit limit

Payment delay indicators (PAY_1–PAY_6)

Actions:

Preserved extreme values (financial data naturally exhibits heavy tails).

Adapted normalization and transformations during modelling where necessary.

Considered skewness when creating descriptive summaries and visualizations.

### 5. Data Type & Formatting Corrections

Ensured that categorical variables (sex, education, marriage) were consistently coded.

Payment history features were treated as ordinal variables.

Target variable converted to integer if required by modelling.

Reorganized feature groups for clarity in analysis.

### 6. Normalization & Standardization

Applied scaling and preprocessing for modelling:

Standardized continuous variables (credit limit, bill amounts, payments).

One-hot encoding performed for required categorical variables.

Training/test split applied for modelling integrity.

#### Results
Descriptive Analysis

Payment history is the strongest raw indicator of default.

Higher credit limits correspond to lower default rates.

Age distribution shows younger clients default more frequently.

### Inferential Statistics

Statistical procedures included:

Confidence intervals for population means

Hypothesis testing for group differences

Interpretation of Type I/II errors

Effect sizes (e.g., Cramer’s V, Cohen’s d)

Findings validated that many behavioural and financial differences between defaulters and non-defaulters are statistically significant.

### Predictive

Two core models were evaluated:
| Model                        | Strength                       | Notes              |
| ---------------------------- | ------------------------------ | ------------------ |
| **Logistic Regression**      | Interpretable coefficients     | Serves as baseline |
| **Random Forest Classifier** | Higher performance, non-linear | Best recall & AUC  |


##### Additional components:

ROC & Precision–Recall curves

Threshold tuning using Youden’s J statistic

SHAP values for global and local explanations

#### Causal Inference (Introductory)

Causal analysis explored:

Defining a "treatment" (e.g., high vs low credit limit)

Propensity score modelling

Overlap evaluation

IPW (Inverse Probability Weighting) estimation

This section is educational and demonstrates key assumptions such as unconfoundedness and positivity.

### Overall Result Summary
| Category            | Issue Addressed       | Outcome                              | Method                  |
| ------------------- | --------------------- | ------------------------------------ | ----------------------- |
| Data Structure      | Mixed variable types  | Clean, organized feature groups      | Inspection + formatting |
| Missing Values      | None present          | N/A                                  | Verification            |
| Outliers            | Heavy financial tails | Modeled with scaling/transformations | Distribution checks     |
| Class Imbalance     | Default ≈ 22%         | Handled with threshold tuning        | ROC/PR evaluation       |
| Predictive Accuracy | Balanced metrics      | Strong RF performance                | Cross-validation        |
| Interpretability    | Complex model         | SHAP explanations                    | Feature importance      |



#### Visuals that support the analysis:

Heatmap of correlations (bill amounts & payments dominate)

ROC and PR curves comparing models

SHAP summary plot for feature influence

Default rate by age, credit limit, or payment delay

Logistic regression coefficient bar chart

### Discussion

The analytical workflow resolved structure, scaling, and formatting inconsistencies, resulting in a dataset well-suited for statistical and machine learning tasks. Descriptive and inferential analysis highlighted risk patterns such as payment history and credit limit. Predictive modelling demonstrated strong performance, with the Random Forest achieving high recall and AUC.

Some limitations were observed:

Class imbalance affects sensitivity (recall)

Raw financial features remain heavy-tailed

Causal inference depends heavily on unverifiable assumptions

No feature engineering beyond standard preprocessing

Future improvements:

SMOTE or re-weighting to address imbalance

Feature engineering (ratios, trend indicators, behavioural flags)

Domain-driven thresholds for risk grouping

More robust causal frameworks (e.g., matching, doubly robust estimation)

### Conclusion

The analytical procedures produced a clean, structured, and highly informative dataset suitable for descriptive, inferential, predictive, and causal tasks. The combination of statistical foundations and advanced modelling ensures reproducibility, transparency, and educational value.

The notebook establishes a strong framework for:

Exploratory data analysis

Hypothesis-driven reasoning

Machine learning model development

Interpretability techniques

Introductory causal effect estimation

This forms a solid foundation for credit risk modelling, academic assessment, and further research extensions.
