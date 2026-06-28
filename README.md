# 💳 YouthPay – Pakistani Financial Intelligence Engine

> A single-file financial dashboard built for Pakistani teenagers and their parents.  
> No installation. No server. No signup. Just open the HTML file in a browser.

---

## 🚀 How to Run

1. Download **`youthpay.html`**
2. Double-click it — it opens in your browser (Chrome, Edge, or Firefox)
3. That's it. Everything works offline.

---

## 📌 What It Does

YouthPay automatically reads bank transaction notifications and turns them into a clear, easy-to-understand financial dashboard — designed specifically for a 15-year-old teenager and their parent/guardian.

---

## 👤 The User — Haniya Ahmed

| Field | Detail |
|-------|--------|
| Name | Haniya Ahmed |
| Age | 15 years old |
| City | Karachi |
| Monthly Allowance | PKR 10,000 |
| Persona | Impulse buyer, coffee lover, MINISO & makeup fan |
| Goal | Understand spending and build better financial habits |

Haniya's **real transaction data** (159 transactions across June 2026) is pre-loaded into the dashboard so it works immediately without any setup.

---

## ✨ Features

### 📊 Dashboard
- **Current Balance** — live balance that updates with every transaction (credits add, debits subtract)
- **Money In / Money Out / Savings %** — clear summary at a glance
- **Financial Health Score** — 0 to 100 score based on savings rate, overspending, late-night habits, and category diversity
- **Spending Breakdown** — visual progress bars showing where money goes by category
- **Daily Spending Trend** — line chart across the month
- **Category Pie Chart** — donut chart of spending split
- **Top Merchants Bar Chart** — which places get visited and spent at most

### 💡 Smart Insights (auto-generated)

| Insight | Trigger |
|---------|---------|
| 🚨 Overspending Alert | Spending exceeds income |
| ☕ Coffee Addiction | Coffee > 8% of total spending |
| 💄 Beauty Budget Warning | Beauty > 15% of total spending |
| 🌙 Late Night Spending | 11pm–4am purchases > 20% of total |
| 🎉 Weekend Splurge | Weekend spending > 1.3x weekday |
| 🔄 Favourite Spot | Any merchant visited 5+ times |
| 📚 Education Reward | Positive note for education spending |
| 💡 Savings Tip | When savings rate < 10% |

### 👥 Two View Modes
- **Teen View** 🎮 — friendly language, emojis, relatable framing
- **Parent View** 🛡️ — formal summary, guardian banner, professional tone

### 🌙 Dark / Light Mode
Full theme toggle — all charts re-render automatically in the correct colours.

### 📂 Import Your Own Data

#### Excel / CSV Upload
Supports any bank statement export. The parser automatically detects column names including:

| Accepted Column Names | Maps To |
|----------------------|---------|
| `merchant_name`, `description`, `narration`, `particulars`, `payee` | Merchant |
| `amount_pkr`, `amount`, `value` | Amount |
| `debit`, `withdrawal`, `dr` | Debit column |
| `credit`, `deposit`, `cr` | Credit column |
| `direction` | `debit` / `credit` type |
| `date_time`, `date`, `transaction_date` | Date |
| `category` | Category (auto-guessed if missing) |
| `source`, `bank` | Bank name |
| `payment_method`, `method` | Payment method |

Supports the exact format of `YouthPay_Hackathon_Dataset_Haniya_Final.xlsx` — just upload it and data merges automatically.

#### Bank Email Upload (.eml)
Export transaction alert emails from Gmail or Outlook and upload them as `.eml` files.

Supported banks and EMIs:
- HBL, MCB, UBL, Meezan Bank
- Bank Alfalah, NayaPay
- Easypaisa, JazzCash

The parser extracts: merchant name, amount, debit/credit type, bank, date, and auto-categorises the transaction.

#### Manual Entry
Add any transaction by hand using the form in the Import panel. Features:
- **SMS auto-parse** — paste a bank SMS text into the Note field and the form auto-fills merchant, amount, type, and category
- Choose category from a dropdown
- Date & time picker defaults to right now

---

## 🗂️ Transaction Categories

| Icon | Category | Examples |
|------|----------|---------|
| 🍔 | Food & Drinks | KFC, OPTP, School Cafeteria |
| ☕ | Coffee | Coffee Wagera, Chai Spot |
| 💄 | Beauty & Makeup | WB by Hemani, Bagallery |
| 🛍️ | Lifestyle | MINISO PK, MINISO Lucky One |
| 🎬 | Entertainment | Atrium Cinema |
| 🚗 | Transport | inDrive, Yango, Careem |
| 📚 | Education | Liberty Books |
| 💡 | Utilities | Easyload |
| 💰 | Allowance / Income | Pocket Money from Parents |
| 💸 | Transfers | Ayesha (Lunch Share) |

---

## 🏦 Data Source

The dashboard is pre-loaded with Haniya Ahmed's dataset from:

```
YouthPay_Hackathon_Dataset_Haniya_Final.xlsx
Sheet: Structured_Transactions
Columns: date_time, source, raw_notification, merchant_name,
         amount_pkr, direction, payment_method, category, city
Total rows: 159 transactions (June 2026)
```

---

## ⚖️ Balance Logic

```
Current Balance = Total Credits (Money In) − Total Debits (Money Out)
```

- Every **credit** (allowance, transfer received) **increases** the balance ↑
- Every **debit** (purchase, payment sent) **decreases** the balance ↓
- Balance shown in **cyan** when positive, **red** when negative

---

## 🧮 Health Score Formula

The score (0–100) is calculated as:

| Factor | Effect |
|--------|--------|
| Base score | +50 |
| Savings rate (up to 40%) | Up to +20 |
| Spending > 2× income | −20 |
| Spending > income | −10 |
| Coffee > 10% of spending | −5 |
| Beauty > 20% of spending | −5 |
| Late-night spend > 25% | −5 |
| Has education spending | +5 |

| Score | Label |
|-------|-------|
| 75–100 | Excellent ✅ |
| 50–74 | Good 🟡 |
| 40–49 | Fair 🟠 |
| Below 40 | Needs Work 🔴 |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| UI | Pure HTML + CSS + Vanilla JavaScript |
| Charts | Chart.js 4.4 (loaded from CDN) |
| Excel parsing | SheetJS / xlsx 0.18 (loaded from CDN) |
| Data | JSON embedded directly in the HTML file |
| Backend / Server | None — fully client-side |

> Requires an internet connection only to load Chart.js and SheetJS from CDN on first open.
> After that it works offline if those scripts are cached by the browser.

---

## 📁 File Structure

```
youthpay.html     ← The entire application (one file, ~76 KB)
README.md         ← This file
```

---

## 🔮 Possible Future Improvements

- Gmail OAuth integration — auto-fetch transaction emails from inbox
- Monthly budget setter with alerts when a category goes over budget
- Recurring transaction detection (e.g. monthly subscriptions)
- Export filtered transactions as CSV
- Multi-month comparison view
- WhatsApp bank alert parsing
- Persistent storage using localStorage so data survives page refresh

---

## 👩‍💻 Built For

**YouthPay Hackathon** — Pakistani Financial Intelligence Engine

Designed to help young Pakistanis understand their money and build healthy financial habits from an early age.
