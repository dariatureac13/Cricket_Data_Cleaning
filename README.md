# Test Cricket Player Data Cleaning
> *A data cleaning and feature engineering workflow designed to standardize historical test cricket performance metrics for downstream statistical modeling.*

---

## ⚙️ Project Type Flag

 - Data Cleaning / Wrangling


---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Workflow](#5-data-workflow)
6. [Key Insights](#9-key-insights)
7. [Assumptions & Limitations](#11-assumptions--limitations)


---

## 1. Project Overview


**Context:** Historical sports data often contains inconsistent naming conventions, missing values, non-standardized delimiters, and composite fields that hinder direct exploratory analysis. This project analyzes a dataset containing performance metrics of international Test Cricket players.

**Problem Statement:** Raw sports records were unformatted, featuring composite string timelines (e.g., career spans), inconsistent null representation in performance metrics, and duplicate records for prominent players.

**Approach:** Using Python and Pandas, the data was parsed via strict delimiter settings, string manipulation was performed to parse multi-value metrics into granular fields, and null imputations were carried out systematically.

**Outcome:** Produced a fully standardized, cleaned dataset ready for comparative statistical analysis and machine learning workflows, free of duplicate records and structural field ambiguities.

---

## 2. Objectives

- **Primary Objective:** Clean and standardize the raw Test Cricket dataset to achieve complete structural integrity for data modeling.


## 3. Project Scope & Tools

### Scope


| Dimension | Details |
|-----------|---------|
| **In Scope** | Processing raw records in CricketTestMatchData.csv, handling missing values, standardizing column names, career timeline splitting, duplicate removal. |
| **Time Period** | Historical Test Cricket records up to current entries in the source dataset. |
| **Granularity** | Player-level career aggregates. |

### Tools & Technologies

| Category | Tool(s) Used |
|----------|-------------|
| Data Storage |  CSV files |
| Data Processing | Python, Pandas |
| Analysis | Pandas |
| Version Control |  Git / GitHub |
| Documentation | Markdown |

---

## 4. Repository Structure

```
[project-root]/
│
├── data/
│   ├── CricketTestMatchData.csv               
│
├── notebooks/
│   ├── CricketCleaningData.ipynb             
└── README.md                 
```

---

## 5. Data Workflow

```
[CricketTestMatchData.csv]
      ↓
[Pandas CSV Ingestion (Semicolon Delimited)]
      ↓
[Column Renaming & Null Imputation]
      ↓
[Duplicate Removal & String Parsing]
      ↓
[Cleaned Dataframe Output]
```

1. **Source:** CricketTestMatchData.csv (semicolon-separated raw historical dataset).
2. **Ingestion:** Loaded into Python using pandas.read_csv() with specified ; delimiter.
3. **Cleaning:** Addressed missing metrics in strike rates and balls faced; executed df.drop_duplicates().
4. **Transformation:** Renamed shorthand column headers (e.g., Mat → Matches) and extracted Rookie_Year and Final_Year from Span.
5. **Analysis:** Validated structural completeness using .isnull().any() and checked record uniqueness.
6. **Output:** Formatted Pandas DataFrame ready for exported tabular storage or downstream analysis.

---




## 9. Key Insights


**Insight 1: Inconsistent Record Capturing Across Eras**
Older cricket records contained a higher frequency of missing Balls_Faced metrics compared to modern entries, requiring explicit imputation to prevent calculation failures.

**Insight 2: Multiple Entry Duplications**
Key historical players (e.g., GA Headley, GS Sobers, JB Hobbs, YBK Jaiswal) appeared multiple times in raw exports due to non-standardized logging from mixed source feeds.

**Insight 3: Composite Fields Bottlenecking Temporal Analysis**
Storing debut and retirement years in a single string field (Span) blocked direct timeline grouping and longevity calculations until parsed into discrete integers.



## 11. Assumptions & Limitations

### Assumptions
- Records with missing Balls_Faced or Batting_Strike_Rate were treated as 0 for quantitative continuity.
- Player names in the dataset were assumed to be unique identifiers after exact duplicate deletion.

### Limitations
- Historical gaps exist where ball-by-ball tracking was not recorded in early Test Cricket eras.
- Highly detailed match-by-match breakdowns are absent; data represents career aggregate figures.



