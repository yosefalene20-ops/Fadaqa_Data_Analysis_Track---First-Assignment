# Secure Life General Hospital — Operational & Financial Analytics Capstone

## Project Overview
This repository contains a comprehensive healthcare data analysis and interactive executive dashboard created for **Secure Life General Hospital**. Using a dataset of 1,000 patient records, this project identifies operational bottlenecks in bed utilization, evaluates revenue cycle management efficiencies, and provides actionable, data-driven recommendations for hospital leadership.

---

## Executive Summary & Key Findings (Objective 10)
1. **Revenue Cycle & Collections Focus:** High-cost specialty departments (such as Cardiology and Orthopedics) exhibit a high volume of outstanding and pending balances. Standardizing automated billing follow-ups and insurer claims processing will directly improve cash flow.
2. **Bed Turnover & Capacity Management:** Certain inpatient departments show elevated Average Length of Stay (LOS). Optimizing discharge planning workflows is recommended to increase bed turnover and reduce patient boarding.
3. **Data Quality & EHR Validation:** Data cleaning identified critical input errors in raw patient records (e.g., insurance coverage entered as `7000%` and missing age brackets). Implementing strict form field validation rules in the hospital's Electronic Health Record (EHR) system will prevent downstream financial reporting errors.

---

## Objectives & Analytical Summary

| Objective | Business Question | Solution Method / Formula | Key Visual |
| :--- | :--- | :--- | :--- |
| **Q1** | Total Patient Visits | `=COUNTA(A2:A1001)` | Scorecard KPI |
| **Q2** | Busiest Departments | Pivot Table (`COUNTA of Patient ID`) | Horizontal Bar Chart |
| **Q3** | Highest Billed Departments | Pivot Table (`SUM of Total Bill Amount`) | Column Chart |
| **Q4** | Average Length of Stay | Pivot Table (`AVERAGE of Length of Stay`) | Column Chart |
| **Q5** | Payment Status Proportion | `=COUNTIF(Status, "Paid") / COUNTA(ID)` | Donut Chart |
| **Q6** | Total Billed vs. Outstanding | `=SUM(Bill Amount)` vs. `=SUM(Outstanding)` | Scorecards & Ratio |
| **Q7** | Insurance Coverage Variations | Pivot Table Heatmap (`Dept` vs `Diagnosis`) | Conditional Color Scale |
| **Q8** | Patient Volume by Age Group | Pivot Table (`Age Category`) with Manual Sort | Ordered Bar Chart |
| **Q9** | Admissions & Billing Over Time| Pivot Table (`Admission Month`) | Dual-Axis Combo Chart |
| **Q10** | Management Action Areas | Strategic Narrative Synthesis | Executive Summary |

---

## Dataset & Calculated Fields

The project dataset spans 1,000 patient records (`PAT-3001` through `PAT-4000`). Data cleaning and helper columns were established to facilitate accurate analysis:

* **Column L (`Age Category`):** Cleaned age groupings (`UNDER 18`, `BTW 18 & 35`, `BTW 36 &50`, `BTW 51 &65`, `66 & ABOVE`).
* **Column M (`Length of Stay`):** Calculates admission duration (`=F2-E2`).
* **Column N (`Insurance Covered Amount`):** Total amount paid by insurance (`=I2 * J2`).
* **Column O (`Patient Out-of-Pocket`):** Remaining patient financial obligation (`=I2 - N2`).
* **Column P (`Outstanding Balance`):** Actual uncollected balance based on payment status (`=IF(K2="Paid", 0, IF(K2="Pending", I2, O2))`).
* **Column Q (`Admission Month`):** Helper column for time series analysis (`=TEXT(E2, "YYYY-MM")`).

---

## Dashboard Architecture

The **`Analysis`** tab is structured as an interactive executive dashboard featuring:
* **KPI Header Cards:** Real-time visibility into Patient Volume, Billed Revenue, Total Outstanding Debt, and Collection Efficiency Rate.
* **Operational Performance Grid:** Interactive visual breakdown of department volume, average length of stay, and demographic distributions.
* **Financial Performance Grid:** Revenue per department, payment status share, and multi-month billing trends.
* **Interactive Slicers:** Dynamic filtering by `Department` and `Payment Status`.

---

## Submission & Repository Structure

```text
├── README.md                                    # Project documentation & summary
├── Secure_Life_General_Hospital_Analysis.xlsx   # Main Excel workbook
└── Dashboard_Preview.png                        # Interactive dashboard screenshot

Author
Name: Yosef Alene Woldeyohannes
Program: FadaQa Tech Scholarship Program (FSP 2.0) — Data Analysis Track
Submission Date: March 2026
