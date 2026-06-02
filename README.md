# Credit Risk Prediction Using Alternative Transaction Data

## Project Description

This project focuses on developing a complete credit risk prediction system using alternative transaction data collected from an eCommerce platform. The objective is to estimate the probability that a customer will default on credit obligations, particularly in situations where traditional credit history is unavailable.

The solution covers the entire machine learning lifecycle, including data preparation, feature engineering, creation of a proxy target variable, model training and evaluation, API deployment, and MLOps practices such as experiment tracking, automated testing, and continuous integration/continuous deployment (CI/CD).

## Repository Organization

* **data/** – Contains raw datasets and processed data files.
* **notebooks/** – Includes exploratory data analysis (EDA) notebooks and research work.
* **src/** – Holds source code for preprocessing, feature engineering, model training, prediction, and API services.
* **tests/** – Stores unit and integration tests.
* **.github/workflows/** – Contains CI/CD workflow configurations.
* **Dockerfile** and **docker-compose.yml** – Define the containerization and deployment environment.

---

# Business Understanding of Credit Scoring

## 1. Basel II Requirements and Model Explainability

The Basel II framework highlights the importance of sound risk management, transparency, and regulatory compliance within financial institutions. Since credit scoring models directly influence lending decisions, organizations must be able to explain how risk assessments are generated.

An interpretable model enables financial institutions to justify credit decisions, perform effective model monitoring, and satisfy regulatory audit requirements. Transparency is especially important because regulators, business stakeholders, and customers may require insight into the factors influencing credit risk predictions.

For this reason, financial institutions often favor simpler and more interpretable models, even when more complex algorithms may provide marginally higher predictive accuracy.

## 2. Use of Proxy Variables and Associated Business Risks

The available dataset does not contain a direct indicator of loan default. Because supervised learning techniques require labeled outcomes, a proxy target variable must be constructed to approximate customer credit behavior.

In this project, customer activity patterns derived from Recency, Frequency, and Monetary (RFM) metrics are used to identify potential high-risk and low-risk customer segments. These generated labels serve as a substitute for actual default information during model training.

However, relying on proxy targets introduces uncertainty. The generated labels may not accurately reflect real repayment behavior, which can result in classification errors. Such inaccuracies may cause trustworthy customers to be denied credit or high-risk customers to receive approval, potentially affecting profitability, customer satisfaction, and fairness in lending practices.

## 3. Balancing Explainability and Predictive Performance

A key challenge in credit risk modeling is finding the right balance between model interpretability and predictive power.

Traditional approaches, such as Logistic Regression combined with Weight of Evidence (WoE) encoding, provide a high degree of transparency. These models are easier to explain, validate, and document, making them well-suited for regulated financial environments.

Conversely, advanced machine learning techniques such as Gradient Boosting and XGBoost can capture complex relationships within customer behavior data and often deliver superior predictive performance. Despite their effectiveness, these models are generally less transparent and may present challenges when explaining decisions to regulators and stakeholders.

Selecting the most appropriate model therefore requires careful consideration of regulatory requirements, business objectives, model transparency, fairness, and predictive accuracy.

---

# Dataset Information

The dataset used in this project is sourced from the **Xente Challenge**, a Kaggle competition focused on financial inclusion and credit risk assessment.

Dataset URL:

https://www.kaggle.com/competitions/xente-challenge/data

## Getting Started

1. Create or sign in to your Kaggle account.
2. Accept the competition terms and conditions.
3. Download the dataset files, including `transactions.csv`.
4. Place the downloaded files in the `data/raw/` directory.
5. Execute the preprocessing script located at `src/preprocess.py`.
6. The processed datasets will be generated automatically in the `data/processed/` directory.

---

# Development Guidelines

## Branching Strategy

* The **main** branch should always contain stable and production-ready code.
* New features and enhancements should be developed in dedicated branches following the format:

```text
feature/<feature-name>
```

* Changes should be integrated into the main branch through pull requests and code reviews.

## Code Quality Standards

* Follow the **PEP 8** Python style guide.
* Format code using **Black**.
* Perform static analysis with **Flake8** before committing changes.
* Use type annotations wherever appropriate to improve code readability and maintainability.

## Commit Message Convention

Adopt the Conventional Commits specification:

```text
type(scope): short description
```

Examples:

```text
feat(model): add xgboost training pipeline
fix(api): handle missing customer inputs
docs(readme): update project setup instructions
```

## Testing Requirements

* Add all tests under the `tests/` directory.
* Ensure that all unit and integration tests pass successfully using:

```bash
pytest
```

* Verify test results locally before pushing code or creating a pull request.
