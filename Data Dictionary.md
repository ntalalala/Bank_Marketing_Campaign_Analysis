# Bank Marketing Dataset – Data Dictionary

## Overview
This document describes the schema, variables, data types, and meanings of the **Bank Marketing Dataset**.

---

## Data Dictionary

| No. | Schema | Table | Variable | Description | Data Type | Measurement Scale | Values | Notes |
|----|--------|-------|----------|-------------|-----------|-------------------|--------|-------|
| 1 | Database | Bank | `age` | Customer age | Numeric | Interval / Quantitative | – | |
| 2 | Database | Bank | `job` | Type of job | String | Nominal / Qualitative | admin, blue-collar, entrepreneur, housemaid, management, retired, self-employed, services, student, technician, unemployed, unknown | |
| 3 | Database | Bank | `marital` | Marital status | String | Nominal / Qualitative | divorced, married, single, unknown | |
| 4 | Database | Bank | `education` | Education level | String | Ordinal / Qualitative | basic.4y, basic.6y, basic.9y, high.school, illiterate, professional.course, university.degree, unknown | |
| 5 | Database | Bank | `default` | Has credit in default (failure to meet debt payments) | String | Nominal / Qualitative | yes, no, unknown | |
| 6 | Database | Bank | `housing` | Has a housing loan | String | Nominal / Qualitative | yes, no, unknown | |
| 7 | Database | Bank | `loan` | Has a personal loan | String | Nominal / Qualitative | yes, no, unknown | |
| 8 | Database | Bank | `contact` | Contact communication type of the last campaign | String | Nominal / Qualitative | cellular, telephone | |
| 9 | Database | Bank | `month` | Month of last contact | String | Ordinal / Qualitative | jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec | |
| 10 | Database | Bank | `day_of_week` | Day of week of last contact | String | Ordinal / Qualitative | mon, tue, wed, thu, fri | |
| 11 | Database | Bank | `duration` | Duration of last contact (in seconds) | Numeric | Ratio / Discrete / Quantitative | – | |
| 12 | Database | Bank | `campaign` | Number of contacts during this campaign (including last contact) | Numeric | Interval / Discrete / Quantitative | – | |
| 13 | Database | Bank | `pdays` | Days since last contact from a previous campaign | Numeric | Ratio / Discrete / Quantitative | 999 = client not previously contacted | |
| 14 | Database | Bank | `previous` | Number of contacts before this campaign | Numeric | Interval / Discrete / Quantitative | – | |
| 15 | Database | Bank | `poutcome` | Outcome of the previous marketing campaign | String | Ordinal / Qualitative | failure, nonexistent, success | |
| 16 | Database | Bank | `emp.var.rate` | Employment variation rate (quarterly indicator) | Numeric | Ratio / Continuous / Quantitative | – | |
| 17 | Database | Bank | `cons.price.idx` | Consumer Price Index (monthly price changes) | Numeric | Ratio / Continuous / Quantitative | – | |
| 18 | Database | Bank | `cons.conf.idx` | Consumer Confidence Index (economic sentiment) | Numeric | Continuous / Quantitative | – | |
| 19 | Database | Bank | `euribor3m` | 3-month Euribor interest rate | Numeric | Continuous / Quantitative | – | |
| 20 | Database | Bank | `nr.employed` | Number of employees (quarterly indicator) | Numeric | Ratio / Continuous / Quantitative | – | |
| 21 | Database | Bank | `y` | Has the client subscribed to a term deposit? (Target variable) | Boolean / Categorical | Nominal | yes, no | Target variable |

---

## Notes
- Categorical variables may require encoding (e.g., one-hot or ordinal encoding) before modeling.
- The variable `duration` should be used with caution, as it is known only after the call is performed.
- The target variable for prediction tasks is **`y`**.

