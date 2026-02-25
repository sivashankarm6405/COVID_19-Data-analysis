
# 🦠 COVID-19 Data Analysis System — SQL Project

A beginner-to-intermediate SQL project that analyzes COVID-19 infection rates, vaccination progress, and regional comparisons using structured query language.

Built as part of a 10-project SQL portfolio series.

---

## 📊 What This Project Does

This project builds a complete COVID-19 data analysis system using two relational tables and 18 SQL queries that cover everything from basic filtering to multi-table joins and calculated metrics.

The final output is a **dashboard query** that shows every country's confirmed cases, death rate, infection spread, and vaccination coverage — all in a single view.

---

## 🗂️ Dataset

- **Source:** Johns Hopkins University COVID-19 Data Repository
- **Countries covered:** USA, India, Brazil, UK, Germany
- **Time periods:** January 2021, June 2021, December 2021
- **Tables:** `covid_data`, `vaccination_data`

> In production, replace sample data by loading real CSVs directly from the [Johns Hopkins GitHub repo](https://github.com/CSSEGISandData/COVID-19).

---

## 🧠 SQL Concepts Covered

| Concept | Used In |
|---|---|
| `CREATE TABLE`, `INSERT` | Steps 1–2 |
| `WHERE`, `GROUP BY`, `HAVING` | Step 3 |
| Arithmetic in SELECT (`ROUND`, `*`, `/`) | Step 4 |
| `SUM`, `MAX`, `AVG` aggregations | Steps 3–5 |
| `JOIN` (self join & two-table join) | Steps 6–8 |
| `ORDER BY`, `LIMIT` | Throughout |
| `CREATE VIEW` | Dashboard View |

---

## 📁 Project Structure

```
covid19-sql-analysis/
│
├── covid19_analysis_project.sql     # Main project — all 18 queries
├── covid19_dashboard_view.sql       # CREATE VIEW for the dashboard query
├── covid_dashboard_data.csv         # Sample dataset (importable to Power BI / Tableau)
└── README.md                        # This file
```

---

## 🔍 Queries Breakdown

### 🟢 Basic (WHERE & HAVING)
- Q1: Total confirmed cases per country
- Q2: Countries with 10M+ confirmed cases
- Q3: Filter data for a specific date
- Q4: Countries where deaths exceeded 100,000

### 🟡 Infection Rate Analysis
- Q5: Cases & deaths per 100,000 population
- Q6: Case Fatality Rate (CFR %) by country
- Q7: Recovery rate per country

### 🟡 Regional Comparisons
- Q8: Total cases grouped by region
- Q9: Best and worst regions by fatality rate

### 🟠 Time Series Analysis
- Q10: Case growth over time per country
- Q11: New cases between two date periods

### 🟠 Vaccination Progress
- Q12: Vaccination coverage by country
- Q13: Countries with 50%+ full vaccination
- Q14: Vaccination growth (June vs December)

### 🔴 Dashboard
- Q15: Full dashboard — cases + vaccination combined
- Q16: Global totals summary
- Q17: Top 3 most affected countries
- Q18: Top 3 countries by vaccination coverage

---

## 🖥️ Dashboard View

The `covid_dashboard` VIEW combines both tables and pre-calculates all key metrics:

```sql
SELECT * FROM covid_dashboard
WHERE report_date = '2021-12-01'
ORDER BY confirmed DESC;
```

**Output includes:** `country`, `region`, `confirmed`, `deaths`, `cfr_pct`, `cases_per_100k`, `fully_vaccinated_pct` and more.

---

## ⚙️ How to Run

1. Open **MySQL Workbench**, **DBeaver**, or any SQL editor
2. Run `covid19_analysis_project.sql` from top to bottom
3. Run `covid19_dashboard_view.sql` to create the VIEW
4. Execute individual queries to explore the data

> Tested on **MySQL 8.0**. Minor syntax adjustments may be needed for PostgreSQL or SQL Server.

---

## 📈 Power BI Dashboard

A Power BI dashboard was built on top of this data using `covid_dashboard_data.csv`.

Visuals include:
- KPI Cards (Total Cases, Deaths, CFR%, Vaccination%)
- Line Chart — Cases over time
- Bar Chart — Confirmed cases by country
- 100% Stacked Bar — Vaccination progress
- Map Visual — Geographic spread

---

## 🚀 Future Improvements

- [ ] Load real-time data from Johns Hopkins GitHub via scheduled import
- [ ] Add `daily_new_cases` column using window functions (`LAG`)
- [ ] Add indexes on `(country, report_date)` for query performance
- [ ] Extend to 50+ countries
- [ ] Add stored procedures for automated reporting

---

## 👤 Author

**[Siva Shankar M]**
SQL Portfolio Project

---
