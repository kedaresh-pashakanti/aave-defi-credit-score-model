# 📊 Wallet Score Analysis (Aave V2)

This document presents an analysis of the credit scores generated for user wallets based on their transaction behavior on Aave V2.

---

## 🔢 Score Distribution

The 0–1000 credit scores were binned into 10 ranges:

| Score Range | Wallet Count  |
|-------------|---------------|
| 0–100       | X wallets     |
| 100–200     | X wallets     |
| 200–300     | X wallets     |
| ...         | ...           |
| 900–1000    | X wallets     |

📊 **[See plot below for histogram of score distribution]**

![Score Distribution](score_distribution.png)

---

## 🧠 Behavior of Low-Scoring Wallets (0–300)
- Tend to have **low repay-to-borrow ratio**
- Frequently faced **liquidation calls**
- Performed very few unique actions (mostly borrowing)
- Showed sudden activity bursts → **bot-like behavior**

---

## 🛡️ Behavior of High-Scoring Wallets (800–1000)
- Frequently repaid loans (repay/borrow ratio > 0.9)
- Actively used the protocol: deposits, borrows, repays, redeems
- Engaged over longer periods (30+ days span)
- Diverse usage of assets and actions

---

## ✅ Summary

- Isolation Forest detected risky patterns based on 15+ engineered features
- A clear difference was observed in behavioral patterns between low and high score groups
- This analysis provides transparency into how credit scores are determined using only transaction behavior

---


