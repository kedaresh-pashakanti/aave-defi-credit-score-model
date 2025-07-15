# 💳 DeFi Wallet Credit Scoring (Aave V2)

## 🧩 Problem Statement

We are given a dataset of 100,000 transaction-level entries from the Aave V2 protocol. Each entry includes a wallet interacting with the DeFi protocol using actions such as:

- `deposit`
- `borrow`
- `repay`
- `redeemunderlying`
- `liquidationcall`

The task is to build a machine learning model that assigns a **credit score between 0 and 1000** to each wallet. Higher scores reflect responsible usage, while lower scores indicate bot-like, exploitative, or risky behavior.

---

## 🔍 Approach Overview

### ✅ 1. Data Parsing
- Parsed 100K raw transactions from JSON
- Extracted relevant fields:
  - `userWallet`, `timestamp`, `action`, `amount`, `assetSymbol`, `assetPriceUSD`

### ✅ 2. Feature Engineering
For each wallet, we extracted behavioral features such as:
- `total_transactions`
- `num_deposits`, `num_borrows`, `num_repays`, `num_liquidations`
- `repay_to_borrow_ratio`
- `avg_deposit_usd`, `avg_borrow_usd`
- `unique_actions_used`, `unique_assets_used`
- `tx_activity_span_days`

> 📁 Output: `wallet_features.csv`

---

## 🧠 Credit Scoring Model (ML-Based)

Since no labeled ground-truth credit scores were available, we used **unsupervised machine learning**:

### 🔹 Model Used: `Isolation Forest`
- Trained on all wallet features
- Detects anomalies (unusual or risky wallet behavior)
- Wallets with normal behavior → high score
- Wallets flagged as outliers → low score

### 🎯 Scoring Logic:
- Used `model.decision_function()` to compute anomaly score
- Mapped score to range **0–1000** using min-max scaling
- Inverted score so that:
  - 1000 = safest wallet
  - 0 = most risky

> 📁 Final Output: `wallet_scores.csv`

---

## 🛠 How to Run (Google Colab)
1. Upload the provided `user-wallet-transactions.json.zip`
2. Run the feature engineering script to generate `wallet_features.csv`
3. Run the ML scoring script to get `wallet_scores.csv`
4. Download the final file for submission

---

## 📌 Sample Output
| userWallet                             | credit_score c| num_deposits   | num_liquidations  |
|----------------------------------------|---------------|----------------|-------------------|
| 0x00000000001accfa9cef68cf5371a23025...| 964           | 3              | 0                 |
| 0x000000000096026fb41fc39f9875d164b... | 112           | 1              | 2                 |

---

## ✅ Summary
- Extracted and engineered wallet features from DeFi transaction history
- Applied unsupervised ML to detect risky users
- Scaled results to human-readable credit scores (0–1000)
- Created a robust, extensible, and transparent scoring pipeline

---

## ✨ Tools Used
- Python, Pandas, Scikit-learn
- Google Colab for processing
- Isolation Forest for unsupervised anomaly detection

---

## 🙌 Author
Built by [KEDARESH GANESH PASHAKANTI]  
For Internship 
