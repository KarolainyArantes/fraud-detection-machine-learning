# 🕵🏻 Fraud Detection Using Machine Learning

**Version:** 1.0.0 — Initial Release  
**Project Status:** In Progress

## 👁 Overview 

This project explores the use of Machine Learning techniques to identify potentially fraudulent transactions through predictive modeling.

The project follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** methodology, covering business understanding, data understanding, data preparation, modeling, evaluation, and prediction.

The initial version implements a Logistic Regression model with spline-based feature transformations to capture nonlinear relationships in transaction data.

This is an initial experimental version. The project will be continuously improved through further model evaluation, feature engineering, algorithm comparison, and refinement of the fraud detection strategy.

## 🎯 Project Objectives

- Explore transaction patterns and identify potential fraud indicators.
- Perform exploratory data analysis (EDA).
- Prepare and transform data for Machine Learning.
- Develop and evaluate a classification model.
- Analyze the trade-off between precision and recall.
- Generate fraud probability scores for previously unseen transactions.
- Establish a foundation for future improvements in fraud detection.

## ⚙ Methodology

The project follows the CRISP-DM methodology:

1. **Business Understanding:** Define the fraud detection problem and its objectives.
2. **Data Understanding:** Explore transaction characteristics, distributions, and class imbalance.
3. **Data Preparation:** Perform preprocessing, encoding, feature transformations, and data splitting.
4. **Modeling:** Train and compare Logistic Regression configurations.
5. **Evaluation:** Assess model performance using classification metrics and threshold analysis.
6. **Deployment:** Generate predictions for January 2026 transactions.

## 🎲 Dataset

The project uses entirely **synthetic transaction data**, created for educational and portfolio purposes.

The datasets contain fictional customer names, establishments, locations, transaction information, and fraud labels. They do not represent real individuals, businesses, or financial transactions.

| Dataset | Description |
|---|---|
| `transacoes_historico_2025.csv` | Historical labeled transactions used for model development and evaluation. |
| `transacoes_jan2026.csv` | Unlabeled January 2026 transactions used for prediction. |
| `january_2026_fraud_predictions.csv` | January 2026 transactions enriched with predicted fraud probabilities and classifications. |

**Target variable:** `flag_fraude`

The historical dataset contains approximately 523,525 transactions, with a significant class imbalance between legitimate and fraudulent transactions.

## 🏗 Model Development

Six Logistic Regression configurations were compared using 5-fold Stratified Cross-Validation.

The experiments evaluated different feature transformation strategies, including:

- Linear transformations.
- Polynomial transformations.
- Spline transformations.
- Different class weighting configurations.

The selected configuration uses:

- Logistic Regression.
- Spline-based feature transformation.
- `class_weight=None`.
- `max_iter=2000`.
- `solver='lbfgs'`.
- `random_state=42`.

A classification threshold of **0.07** was selected based on the out-of-fold threshold analysis, prioritizing fraud detection recall over precision.

This threshold is an experimental decision for the current version and may change as the project evolves.

## 📊 Model Evaluation

The final model was evaluated on an independent test set.

### Overall Performance

| Metric | Result |
|---|---:|
| ROC-AUC | 0.8634 |
| Average Precision | 0.1484 |

### Performance at the Selected Threshold (0.07)

| Metric | Result |
|---|---:|
| Precision | 15.02% |
| Recall | 66.41% |
| F1-Score | ~24% |
| Accuracy | ~84% |

The selected threshold identifies approximately 66% of fraudulent transactions in the test set, at the cost of generating a considerable number of false positives.

This trade-off reflects the initial strategy of prioritizing the identification of potentially fraudulent transactions.

## 🔮 January 2026 Predictions

The trained model was applied to 44,451 previously unseen transactions from January 2026.

| Classification | Transactions | Percentage |
|---|---:|---:|
| Potential Fraud | 7,575 | 17.04% |
| Legitimate | 36,876 | 82.96% |
| **Total** | **44,451** | **100%** |

The total transaction value associated with the records flagged as potentially fraudulent was **R$ 234,206.73**.

This amount represents the value of flagged transactions, not confirmed financial losses.

Since the January dataset does not contain ground-truth fraud labels, these predictions cannot yet be validated using actual precision, recall, or F1-score.

## 📂 Repository Structure

```text
fraud-detection-machine-learning/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── fraud_detection_crisp_dm.ipynb
│
├── src/
│   ├── preprocessing.py
│   └── model.py
│
├── reports/
│   └── figures/
│
└── data/
    └── README.md
```

## 🛠 Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly
- Jupyter Notebook

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/fraud-detection-machine-learning.git

cd fraud-detection-machine-learning
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the notebook

Open the notebook:

```text
notebooks/fraud_detection_crisp_dm.ipynb
```

Follow the notebook sections to reproduce the data analysis, model development, evaluation, and prediction process.

**Note:** Place the synthetic datasets in the `data/` directory before running the notebook.

## ⚠ Limitations

This first version has some important limitations:

- The model currently uses Logistic Regression as its classification algorithm.
- The dataset is synthetic and may not fully represent real-world fraud patterns.
- The selected classification threshold generates a relatively high number of false positives.
- January 2026 predictions have not been validated against actual fraud outcomes.
- The current implementation is primarily notebook-based and is not yet a production-ready solution.

Therefore, the results should be interpreted as experimental findings rather than evidence of real-world fraud prevention performance.

## ⭐ Future Improvements

The project is planned to evolve through the following steps:

- [ ] **Code modularization:** Move preprocessing and modeling logic into reusable Python modules.
- [ ] **Feature engineering:** Explore additional behavioral, temporal, and transactional features.
- [ ] **Model comparison:** Evaluate alternative algorithms such as Random Forest, XGBoost, LightGBM, and other classification approaches.
- [ ] **Hyperparameter optimization:** Improve model performance through systematic parameter tuning.
- [ ] **Threshold optimization:** Investigate different classification thresholds based on operational costs and business requirements.
- [ ] **Model explainability:** Apply SHAP or similar techniques to understand the factors influencing predictions.
- [ ] **Model calibration:** Evaluate whether predicted probabilities accurately reflect fraud likelihood.
- [ ] **Monitoring:** Develop strategies to monitor model performance and potential data drift.
- [ ] **Deployment:** Explore API-based prediction and integration with an interactive monitoring dashboard.

## 🟡 Project Status

**Version 1.0 — Initial Release**

This repository represents the first version of an ongoing Machine Learning project.

The current objective is to establish a reproducible end-to-end workflow, document the modeling decisions, and create a baseline for future experimentation.

Future versions will focus on improving predictive performance, interpretability, code organization, and practical applicability.

---

*Developed as a Data Science and Machine Learning portfolio project 🕵🏻.*
