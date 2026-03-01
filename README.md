# 💳 Credit Card Fraud Detection using Logistic Regression

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-LogisticRegression-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Kaggle](https://img.shields.io/badge/Dataset-Kaggle-blue?logo=kaggle)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

A machine learning project that detects **fraudulent credit card transactions** using **Logistic Regression**. The dataset is highly imbalanced, so undersampling is applied to create a balanced training set before model training.

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset Features](#-dataset-features)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [How It Works](#-how-it-works)
- [Results](#-results)
- [Predict a Transaction](#-predict-a-transaction)
- [License](#-license)

---

## 📌 Project Overview

Credit card fraud is a serious problem — but fraud cases are extremely rare (less than 0.2% of all transactions). This project:

- Loads and explores the Credit Card Fraud dataset from Kaggle
- Handles the **class imbalance** using undersampling
- Trains a **Logistic Regression** classifier
- Evaluates accuracy on both training and test data
- Allows you to input a custom transaction to check if it's fraud or legit

---

## 📊 Dataset Features

The dataset contains **284,807 transactions** with **31 columns**. The `creditcard.csv` file is included in this repository. Original source: [Credit Card Fraud Detection — Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

| Feature | Description |
|---------|-------------|
| **Time** | Seconds elapsed between this transaction and the first transaction in the dataset. |
| **V1 – V28** | Anonymized features obtained via **PCA (Principal Component Analysis)**. The original features are hidden for confidentiality. These 28 components capture patterns in spending behavior. |
| **Amount** | The transaction amount in dollars. This is a real, non-anonymized feature. |
| **Class** *(target)* | `0` = Legitimate transaction, `1` = Fraudulent transaction. This is what the model predicts. |

> ⚠️ **Class Imbalance:** Only **492 out of 284,807** transactions are fraud (~0.17%). Without balancing, a model could achieve 99.8% accuracy by always predicting "legitimate" — which is useless. We fix this with undersampling.

---

## 📁 Project Structure

```
credit-card-fraud-detection/
│
├── credit_card_fraud_detection.ipynb   # Main Jupyter notebook
├── creditcard.csv                      # Dataset (download from Kaggle)
├── requirements.txt                    # Python dependencies
└── README.md                           # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- pip

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/credit-card-fraud-detection.git
   cd credit-card-fraud-detection
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook credit_card_fraud_detection.ipynb
   ```

> **Google Colab users:** The notebook loads the CSV directly from GitHub — no uploads needed, just run all cells.

---

## ⚙️ How It Works

```
Raw Dataset (284,807 rows)
        │
        ├── Legit transactions  → 284,315 rows
        └── Fraud transactions  →     492 rows
                │
                ▼
        Undersampling: randomly sample 492 legit rows
                │
                ▼
        Balanced Dataset: 492 legit + 492 fraud = 984 rows
                │
                ▼
        Train/Test Split (80/20, stratified)
                │
                ▼
        Logistic Regression Model
                │
                ▼
        Predict: Legitimate ✅ or Fraudulent 🚨
```

---

## 📈 Results

| Metric | Training Set | Test Set |
|--------|-------------|----------|
| Accuracy | ~93–95% | ~91–93% |

The model correctly identifies the majority of both legitimate and fraudulent transactions on the balanced dataset.

---

## 🔮 Predict a Transaction

At the end of the notebook, there is an **interactive input section**. Fill in the feature values and run the cell:

```python
input_data = {
    'Time':   0,
    'V1': -1.3598, 'V2': -0.0727, ...
    'Amount': 149.62
}
```

Output:
```
========================================
  ✅ Transaction is LEGITIMATE
========================================
```
or
```
========================================
  🚨 Transaction is FRAUDULENT
========================================
```

---

## 🛠 Tech Stack

- **Python** — Core language
- **Pandas / NumPy** — Data manipulation
- **scikit-learn** — Logistic Regression, train/test split, accuracy score

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

> Made with ❤️ | Feel free to fork, star ⭐, and contribute!
