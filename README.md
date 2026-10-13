# Zomato SQL Project — Customer & Sales Analysis

A beginner-friendly **SQL** project that builds a small Zomato-style database from scratch and answers business questions about customer spending, visit frequency, product popularity, and gold-membership behaviour using joins, aggregation, and subqueries.

## 📊 About the Database

The database (`Zomatosqlproject`) is created directly inside the notebook with `CREATE TABLE` and `INSERT` statements — no external file needed.

| Table | Columns | Description | Rows |
|---|---|---|---|
| `users` | userid, signup_date | Registered customers | 3 |
| `goldusers_signup` | userid, gold_signup_date | Customers who joined the Gold membership, and when | 2 |
| `sales` | userid, created_date, product_id | Individual purchase records | 16 |
| `product` | product_id, product_name, price | Menu items and their prices | 3 |

## 🎯 Purpose

To practice core SQL skills — `INNER JOIN`, `GROUP BY`, aggregate functions, `ORDER BY`, `LIMIT`, and subqueries — by answering realistic questions a food-delivery business would ask about its customers and menu.

## 🛠️ Approach

1. **Create the database and tables**, then insert the sample data.
2. **Join `sales` with `product`** to attach a price to every purchase.
3. **Aggregate** with `SUM()` and `COUNT()` grouped by customer or product.
4. **Rank** results with `ORDER BY ... DESC` and `LIMIT`.
5. **Use a subquery** to reuse the "most purchased item" result inside a second query.
6. **Join `sales` with `goldusers_signup`** to start analysing behaviour after membership.

## ❓ Questions Answered

| # | Question | Key SQL Concepts |
|---|---|---|
| 1 | What is the total amount each customer spent on Zomato? | `INNER JOIN`, `SUM()`, `GROUP BY` |
| 2 | How many days has each customer visited Zomato? | `COUNT(DISTINCT ...)`, `GROUP BY` |
| 3 | What is the most purchased item, and how many times did each customer buy it? | `COUNT()`, `ORDER BY`, `LIMIT`, subquery |
| 4 | Which item was first purchased by a customer after becoming a member? | `INNER JOIN` on `goldusers_signup` *(in progress — see note below)* |

## 📌 Results

Results below were verified by running the notebook's queries on its sample data.

**Q1 — Total spend per customer**

| userid | total_amt_spent |
|---|---|
| 1 | 5,230 |
| 2 | 2,510 |
| 3 | 4,570 |

**Q2 — Distinct visit days per customer**

| userid | distinct_days |
|---|---|
| 1 | 7 |
| 2 | 4 |
| 3 | 5 |

**Q3 — Most purchased item**

- Product **2 (p2)** is the most purchased item, bought **7 times** in total (p1: 5, p3: 4).
- Purchases of product 2 by customer: user 1 → 3 times, user 2 → 1 time, user 3 → 3 times.

## 🗄️ Tech Stack

- **SQL** (MySQL syntax)
- **Jupyter Notebook** — documenting each query with a step-by-step explanation

## 📁 Repository Structure

```
├── ZomatoSale_sql_EDAproject.ipynb    # Notebook with SQL queries and step-by-step explanations
├── Project_Report.docx                # Full project report
└── README.md
```

## 🚀 How to Run

1. Create a database named `Zomatosqlproject` in MySQL.
2. Run the `CREATE TABLE` and `INSERT` statements from the first section of the notebook.
3. Run each query in order in your MySQL client (Workbench, CLI, etc.).
4. Read the explanation cell below each query for a breakdown of how it works.

## ⚠️ Project Status

Q4 is **work in progress**: the notebook currently contains only the join between `sales` and `goldusers_signup`. It still needs a filter for purchases on/after `gold_signup_date` and a "first purchase per customer" step (for example `MIN(created_date)` or `ROW_NUMBER()`).

---
*A beginner SQL project on customer and sales analysis for a Zomato-style food delivery business.*
