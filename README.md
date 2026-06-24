# 💰 Financial Risk Analysis with Python – Goldman Sachs

A Python-based financial data analytics project that analyzes customer transaction behavior, detects financial risk, and builds customer profiles using Goldman Sachs transactional data.

---

## 📌 Project Overview

As a Financial Data Analyst at Goldman Sachs, this project uncovers patterns in customer financial behavior, account performance, and transaction risks to improve customer service and minimize financial exposure.

Key business questions addressed:
- How do customers interact with different account types (Savings, Loan, Credit)?
- What are the trends in debit vs. credit transactions across segments?
- Which accounts show unusually high risk or inconsistent financial activity?
- What transaction behaviors correlate with lower balances or overdraft incidents?

---

## 🗂️ Dataset

**Goldman Sachs Financial Transactional Data** — 800 transaction records across 194 unique accounts.

| Column | Description |
|---|---|
| TransactionID | Unique identifier for each transaction |
| CustomerID | Unique identifier for each customer |
| AccountID | Unique identifier for each bank account |
| AccountType | Type of account (Savings, Loan, Credit, Current) |
| TransactionType | Nature of transaction (Deposit, Withdrawal, Transfer, Payment) |
| Product | Financial product involved (Credit Card, Mutual Fund, Home Loan, etc.) |
| Firm | Name of the firm where transaction occurred |
| Region | Geographical region (East, West, North, South, Central) |
| TransactionDate | Date of transaction |
| TransactionAmount | Amount involved in the transaction |
| AccountBalance | Account balance after the transaction |
| RiskScore | Risk score associated with the customer or transaction |
| CreditRating | Credit rating score of the customer |
| TenureMonths | Duration (months) customer has held the account |

---

## 🛠️ Tools & Libraries

- **Python** (Jupyter Notebook)
- **Pandas** – data manipulation and cleaning
- **NumPy** – numerical operations
- **Matplotlib & Seaborn** – data visualization
- **SciPy** – hypothesis testing (t-test)

---

## 📋 Tasks Performed

### Task 1: Data Cleaning & Formatting
- Removed special characters from financial fields (`TransactionAmount`, `AccountBalance`, `RiskScore`) using regex
- Converted date column to `datetime` format using `pd.to_datetime()`
- Standardized `AccountType` and `TransactionType` to lowercase using `.str.lower().str.strip()`

### Task 2: Descriptive Transactional Analysis
- Built monthly and yearly pivot tables for credits, debits, and net transaction volume
- Plotted credit vs. debit trends over time (Jan 2023 – Jun 2024)
- Top account by inflow: **ACC46655 (₹7,28,037)** | Bottom: **ACC46953 (-₹24,811)**
- Flagged accounts as **Inactive** if gap between transactions ≥ 60 days

### Task 3: Customer Profile Building
**Activity Level Rubric:** High = >20 transactions | Medium = 10–20 | Low = <10

- Segmented customers into 4 groups by average balance and transaction volume:
  - High Balance – High Volume: 49 accounts
  - Low Balance – Low Volume: 49 accounts
  - Low Balance – High Volume: 48 accounts
  - High Balance – Low Volume: 48 accounts
- Profiled **37 high net inflow accounts** with positive NetInflow
- Identified **35 high-frequency low-balance accounts**
- Flagged negative balance accounts — ACC19178 had avg balance of **-₹1,541**

### Task 4: Financial Risk Identification
- Tracked accounts with large withdrawals (>₹50,000) — flagged **95 suspicious accounts**
- Calculated **balance volatility** using standard deviation and Coefficient of Variation (CV)
- Used **Z-score method** (threshold: |Z| > 3) — no extreme anomalies found in dataset
- Combined risk indicators (large withdrawals + overdrafts + anomalies) to create a Suspicious Flag

### Task 5: Visualisation (EDA)
- Distribution of Transaction Amounts — bell-shaped, medium values most common
- Transaction Type Distribution — balanced mix across all four types
- Monthly Transaction Count Trend — seasonal fluctuations observed
- Transaction Amount vs Account Balance — no strong direct correlation
- Distribution of Balance Volatility (CV) — most accounts show moderate volatility
- Activity Level vs Average Balance — medium-activity accounts more stable
- Risk Score Distribution — most customers fall in the medium risk range (0.3–0.7)

### Task 6: Hypothesis Testing
**H0:** High-volume transaction accounts do NOT have higher average balances than low-volume accounts.

- High-volume avg balance: **₹72,512** | Low-volume avg balance: **₹71,683**
- T-statistic: **0.3151** | P-value: **0.7531**
- **Result: Fail to reject H0** — transaction frequency alone does not significantly influence balance levels

---

## 💡 Key Insights

- 95 accounts were flagged as suspicious based on large withdrawals or overdraft behavior
- Only 1 account (ACC19178) had a negative average balance — a rare but critical risk case
- Transaction frequency does not statistically predict account balance levels (p-value = 0.75)
- Medium-activity accounts maintain more stable and higher average balances
- All four transaction types (deposit, withdrawal, payment, transfer) occur in nearly equal proportions

---

## 📁 Repository Structure

```
goldman-sachs-financial-risk-python/
│
├── python_project.ipynb        # Main Jupyter Notebook (Tasks 1–6)
├── goldman_sachs.csv           # Raw dataset
├── Cleaned_Data.csv            # Task 1 output
├── Task 2_1.csv                # Monthly transaction summary
├── Task 2.4.csv                # Inactive/active account flags
├── Task 3_1.csv                # Activity level segmentation
├── Task 3_2.csv                # Customer segment profiles
├── Task 3_3_1.csv              # High net inflow accounts
├── Task 3_3_2.csv              # High-frequency low-balance accounts
├── Task 3_3_3.csv              # Negative/near-zero balance accounts
├── Task 4_1.csv                # Large withdrawal tracking
├── Task 4_2.csv                # Balance volatility stats
├── Task 4_3.csv                # Suspicious customer flags
├── Final_python_project.pdf    # Summary report
└── README.md
```

---

## 🚀 How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy
   ```
3. Place `goldman_sachs.csv` in the project folder
4. Open `python_project.ipynb` in Jupyter Notebook
5. Run cells sequentially from Task 1 to Task 6

---

## 📄 Recommendations

- Monitor accounts with frequent large withdrawals, overdrafts, or high CV for financial risk
- Target high-value and high-activity customers with personalized retention strategies
- Launch re-engagement campaigns for inactive accounts (gap ≥ 60 days)
- Implement automated dashboards and alerts based on risk indicators to improve fraud detection

---

## 👤 Author

**Yogesh Kadam** — Financial Risk Analysis with Python (Goldman Sachs)

---

## 📄 License

This project was created as part of an Internshala training program. For educational use only.
