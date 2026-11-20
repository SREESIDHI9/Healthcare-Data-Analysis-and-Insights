# Healthcare-Data-Analysis-and-Insights
Healthcare data analytics in Excel: cleaning records, engineering clinical risk tiers, merging tables via VLOOKUP, and building an interactive dashboard with weight and diabetes slicers to uncover age correlations, medical history patterns, and cost drivers.

## Project Overview
This project analyzes a multi-table healthcare dataset covering customer profiles, medical examinations, and hospitalization details to uncover patterns in patient health profiles, medical histories, and healthcare costs. Using Microsoft Excel, raw records are cleaned, standardized, categorized into clinical risk tiers, merged via `VLOOKUP` into a unified `Healthcare` table, and visualized through pivot tables, analytical charts, and an interactive slicer-driven dashboard.

## Objective
* Clean missing and placeholder (`?`) values across medical examination and hospitalization records using rule-based imputation (`Sep` for missing months, rounded average for missing years, mode imputation for categorical tiers, and `Unknown` or appropriate handling for missing `State ID` values).
* Transform customer names into `Title`, `First Name`, and `Last Name`, convert `NumberOfMajorSurgeries` into numeric values, audit `Heart Issues` and `smoker` consistency, derive `Weight Status` and `Diabetes Status`, format `Date of Birth` as `DD-MMM-YYYY`, calculate `Age` relative to **8th June 2023**, and format `charges` in USD (`$`).
* Consolidate all source tables into a `Healthcare` sheet using `VLOOKUP` on `Customer ID` and retain the 17 specified analytical fields.
* Build pivot tables, charts, and an interactive dashboard filtered by `Weight Status` and `Diabetes Status` slicers to evaluate smoking and cancer history, transplant history vs. major surgeries and HbA1C, charges across weight/diabetes categories and hospital tiers/states, and age correlations with BMI, HbA1C, and healthcare charges.

## Dataset Description
The assignment dataset ([Download Dataset](https://drive.google.com/uc?export=download&id=1zelh7bZrE7F290QtTABHgHYn4B7JDbZO)) consists of three relational tables linked by `Customer ID` and merged into a consolidated `Healthcare` table containing `[fill in total record count]` patient records across 17 retained columns:

* **Customer Names:** Contains `Customer ID` and full `name` strings (split into `Title`, `First Name`, and `Last Name`).
* **Medical Examinations:** Contains clinical and history indicators including `BMI`, `HBA1C`, `Heart Issues`, `Any Transplants`, `Cancer history`, `NumberOfMajorSurgeries`, and `smoker`.
* **Hospitalization Details & Cost/Location Attributes:** Contains birth date components (`year`, `month`, `date`), `charges`, `Hospital tier`, `City tier`, and `State ID`.
* **Derived Analytical Columns:** `Weight Status` (`Underweight` `< 18.5`, `Normal Weight` `18.5–24.9`, `Overweight` `25.0–29.9`, `Obesity` `>= 30.0`), `Diabetes Status` (`Normal` `< 5.7`, `Prediabetes` `5.7–6.4`, `Diabetes` `>= 6.5`), `Date of Birth` (`DD-MMM-YYYY`), and `Age` (as of `2023-06-08`).

## Workflow
1. **Data Cleaning:** Audited `?` missing markers across `Medical Examinations` and `Hospitalization Details`; imputed missing `month` values with `Sep` and missing `year` values with the rounded mean year; filled missing `smoker`, `Hospital tier`, and `City tier` values using mode values; and handled missing `State ID` values with `Unknown` (or assigned strategy).
2. **Data Transformation:**
   * Split `names` into `Title`, `First Name`, and `Last Name`.
   * Converted `NumberOfMajorSurgeries` into numeric values by mapping non-numeric entries consistently.
   * Checked `Heart Issues` and `smoker` for inconsistencies and applied corrective rules where needed.
   * Created `Weight Status` from `BMI` and `Diabetes Status` from `HBA1C` using conditional formulas.
   * Combined `year`, `month`, and `date` into `Date of Birth` (`DD-MMM-YYYY`), computed `Age` as of **8th June 2023**, and formatted `charges` as currency (`$`).
3. **Data Consolidation (`Healthcare` Sheet):** Merged all three tables by `Customer ID` using `VLOOKUP` and retained the 17 required columns (`Customer ID`, `First Name`, `BMI`, `HBA1C`, `Heart Issues`, `Any Transplants`, `Cancer history`, `NumberOfMajorSurgeries`, `smoker`, `Weight Status`, `Diabetes Status`, `Date of Birth`, `charges`, `Hospital tier`, `City tier`, `State ID`, `Age`).
4. **Exploratory Analysis & Visualization:** Built pivot tables and charts for:
   * **Pie/Donut charts:** Cancer history distribution across smokers vs. non-smokers; total major surgeries and average HbA1C by transplant history.
   * **Column/Bar charts:** Healthcare charges across `Weight Status` and `Diabetes Status`; average charges by `Hospital tier` across states.
   * **Line/Scatter plots:** Correlations of `Age` with `BMI` and `HBA1C`; relationship between `Age` and `charges`.
5. **Interactive Dashboard:** Consolidated charts onto a dashboard view with slicers for `Weight Status` and `Diabetes Status` connected across visualizations.

## Key Findings
* **Smoking & Cancer History:** `[fill in % of smokers vs. non-smokers with cancer history and key comparison]`.
* **Transplant History, Surgeries & HbA1C:** `[fill in total major surgeries and average HbA1C for patients with transplants vs. without transplants]`.
* **Weight Status, Diabetes Status & Charges:** `[fill in highest- and lowest-cost weight and diabetes segments and average/total charges]`.
* **Hospital Tier & State Cost Variations:** `[fill in state and hospital tier cost patterns or outliers]`.
* **Age Relationships (BMI, HbA1C, and Charges):** `[fill in observed trends or correlations between Age and BMI, HbA1C, and healthcare charges]`.

## Business & Policy Recommendations
* **Targeted Preventive & Screening Programs:** Focus smoking cessation and early cancer screening outreach on high-risk smoker cohorts identified in the donut breakdown, paired with preventive metabolic monitoring for `Prediabetes` and `Obesity` segments.
* **Chronic & Surgical Care Management:** Monitor glycemic control (`HBA1C`) and surgical resource allocation closely for patients with prior transplant histories or multiple major surgeries.
* **Cost Containment & Tiered Care Navigation:** Guide patients toward cost-effective hospital tiers where appropriate and review high-charge state/tier combinations to improve transparency and resource allocation.
* **Data Governance & Intake Validation:** Enforce mandatory structured fields and automated validation rules at data entry to prevent `?` placeholders, inconsistent categorical labels (`Heart Issues`, `smoker`), and missing date or state records.

## Tools Used
* **Microsoft Excel:** Data cleaning, formula transformations (`VLOOKUP`, conditional logic, custom date/currency formatting), Pivot Tables, Pivot Charts, Slicers, and Dashboard design.
* **Google Drive / Assignment Dataset:** Source data distribution.

## Tech Stack & Libraries
* **Spreadsheet & BI Stack:** Microsoft Excel (Formula Engine, PivotTables, Charts, Slicers).
* **Optional Reproducibility / Automation Stack (if extending outside Excel):** Python (`pandas`, `numpy`, `matplotlib`, `seaborn`, `openpyxl`) for scripted validation or cross-checking workbook calculations.

## Repository Structures
```text
healthcare-data-analysis-insights/
├── README.md
├── data/
│   └── raw/
│       └── healthcare_source_dataset.xlsx
├── workbook/
│   └── Excel Module End Assignment - Healthcare.xlsx
├── docs/
│   └── Module End Assignment 1_Excel  - Healthcare Analysis and Insights.pdf
└── visuals/
    ├── dashboard_overview.png
    ├── cancer_and_transplant_charts.png
    ├── charges_by_status_and_tier.png
    └── age_correlation_plots.png
```
---
Author:✏️
Sree Sidhi
