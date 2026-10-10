# Banking SQL Case Study — BigQuery

**Domain:** Retail Banking  
**Tool:** Google BigQuery (Standard SQL)  
**Techniques:** CTEs, Window Functions, Multi-table JOINs, Aggregate Functions, Subqueries

---

## Overview

End-to-end SQL analysis on a 9-table relational banking schema for a leading US retail bank.
Answered 22 business questions across five domains and delivered structured
Observation → Interpretation → Recommendation insights for each.

**Schema tables:** customers · accounts · transactions · loans · loan_payments ·
cards · branches · employees · customer_interactions

---

## Business Domains Covered

| Section | Questions | Focus |
|---|---|---|
| I. Initial Exploration | 3 | Data types, date ranges, branch-account breakdown |
| II. Customer Behaviour | 5 | Balance tiers, transaction frequency, age-based card usage, top customers, multi-loan holders |
| III. Branch Performance | 4 | Account growth, branch scorecard, cumulative transactions, loan portfolio |
| IV. Financial Risk & Revenue | 4 | Default rates by loan type, interest revenue, severely overdue loans, YoY growth |
| V. Customer Service | 2 | Complaint rates per branch, chronic complainers |
| VI. Card Portfolio | 3 | Overleveraged cardholders, monthly card spend, card × transaction type breakdown |

---

## SQL Techniques Used

- **CTEs** — multi-step logic broken into readable, reusable named blocks
- **Window functions** — DENSE_RANK, ROW_NUMBER, LAG, SUM OVER, AVG OVER for ranking, running totals, and YoY comparisons
- **Multi-table LEFT JOINs** — preserving branches/customers with zero matches across dependent tables
- **Pre-aggregation before joining** — avoiding fan-out duplication on one-to-many relationships
- **SAFE_DIVIDE** — protecting against runtime divide-by-zero on rate calculations
- **STRING_AGG with chronological sort** — aggregating complaint months in time order
- **Point-in-time filtering in ON clause** — preventing look-ahead bias in overdue loan analysis

---

## Key Findings

- Top 3 branches generate **46.2% of total active-loan interest revenue** — meaningful concentration risk
- Downtown Miami leads transaction volume with fewer staff than lower-ranked branches — efficiency signal
- West Palm and Kendall Branch flagged independently across **two separate risk metrics** (loan default rates and loan paid rates)
- CREDIT card spend appears in only **3 of 12 months** in 2025 — adoption significantly lagging debit
- 53.6% of Downtown Miami's accounts are FROZEN — operational gap at the network's highest-volume branch

---

## Data Limitations Documented

- `transactions` has no `card_id` — transactions cannot be attributed to a specific card when an account holds multiple card types
- `balance` reflects the linked deposit account, not credit card outstanding debt
- Missing `date_of_birth` (affects age-based analysis) and `opened_date` (affects account vintage analysis) for some customers

---

## Project File

📄 [banking-sql-case-study.pdf](https://github.com/kuldeep-p-a/sql-banking-case-study/blob/main/SCALER_Project_USBank.pdf)

---

## About

Completed as part of the **Scaler Academy DSML Programme** (SQL module assessment).  
Author: Kuldeep P Agarwala | [LinkedIn](https://linkedin.com/in/kagarwala)
