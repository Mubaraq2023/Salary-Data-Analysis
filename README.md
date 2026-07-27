# Salary Data Analysis

Exploratory data analysis of over 22,000 salary records, uncovering how pay varies by job role, company, location, employer rating, and employment type using Python, Pandas, and Seaborn.

## Overview

This project analyzes a dataset of reported salaries across tech job roles in India. The analysis is framed around nine business-style questions — e.g., which job roles and cities pay the most, whether higher-rated companies pay better, and whether employment type (full-time vs. intern vs. contractor) affects salary — rather than just producing charts for their own sake.

## Dataset

- **Source:** `Salary_Dataset_DSL.csv`
- **Size:** 22,770 rows × 8 columns (post-cleaning: ~22,700 rows after outlier removal)
- **Key fields:** `Rating`, `Company Name`, `Job Title`, `Salary`, `Salaries Reported`, `Location`, `Employment Status`, `Job Roles`
- **Job Roles categories (11):** Android, Backend, Database, Frontend, IOS, Java, Mobile, Python, SDE, Testing, Web

## Tools & Libraries

- Python 3
- Pandas & NumPy — data cleaning and aggregation
- Matplotlib & Seaborn — visualization
- Jupyter Notebook

## Data Cleaning

- Filled the single missing `Company Name` value using the column mode
- Verified no duplicate rows
- Removed salary outliers using the IQR (interquartile range) method, visually confirmed with box plots before and after

**Known data limitation:** the `Location` field mixes cities (e.g., Mumbai, Bangalore) with states (e.g., Kerala, Madhya Pradesh), so location-based comparisons in this dataset aren't at a fully consistent geographic granularity.

## Business Questions & Key Findings

**1. Which job roles have the highest average salary?**
Database roles pay the most on average (~₹702,555), followed by SDE (~₹648,183) and IOS (~₹593,214). Python and Testing roles sit at the lower end of the top 10 (~₹449,532 and ~₹464,825 respectively).

**2. Which cities offer the highest average salary?**
Mumbai leads by a wide margin (~₹702,196 average), notably higher than Bangalore (~₹568,223), often assumed to be India's top tech-pay hub in this dataset. Jaipur and Pune follow closely behind Bangalore.

**3. Which 5 companies in New Delhi with a 5-star rating pay the highest and lowest?**
Among New Delhi companies rated 5/5, Hapramp, Trillbit, The Art of Mike Mignola, Silicon Valley Recycling, and Parth Universal offered the highest salaries, while Neo Fitnes, WorkingNation, Hopin (India), Star Catalysts, and Atom 8 offered the lowest — showing that even a top employer rating doesn't guarantee top pay.

**4. Which companies offer the highest average salary overall?**
Several companies (Zenith Technology Solutions, ThoughtMiracles, Kristal.AI, Gurugram University, InsideView) tie at the dataset's salary ceiling of ₹1,500,000 — worth noting these are based on very small sample sizes per company.

**5. Which job title has the most salary reports, and which companies pay best with a reliable sample size (≥20 reports)?**
"Software Development Engineer" has the most reports overall (2,137). Restricting to companies with at least 20 reported salaries (to avoid single-data-point noise), Expedia Group leads at ~₹1,350,000 average, followed by Nokia and Amadeus (~₹1,200,000 each).

**6. Is there a relationship between company rating and salary?**
Essentially none — the correlation between `Rating` and `Salary` is **r ≈ 0.025**, meaning a higher employer rating does not meaningfully predict higher pay in this dataset.

**7. Does employment status affect salary?**
Yes, substantially. Full-time employees earn the most on average (~₹579,306), contractors earn less (~₹501,508), and interns/trainees earn far less (~₹338,354 and ~₹324,303 respectively) — an expected but clearly confirmed pattern.

**8. Which job roles are most common?**
SDE dominates by volume (7,245 records), followed by Android (2,812) and Frontend (2,034). Mobile and Database roles are the least represented (211 and 734 records).

**9. How does average salary trend as company rating increases?**
Plotted as a line chart across all rating values (1.0–5.0) — visually, salary does not show a clean upward trend with rating, consistent with the near-zero correlation found in Q6.

## Mini Dashboard

The notebook closes with a 2×2 dashboard summarizing the overall salary distribution, the rating-vs-salary scatter with trend line, the average salary trend by rating, and the top-paying locations.

## How to Run

1. Clone this repository
   ```bash
   git clone https://github.com/yourusername/salary-data-analysis.git
   cd salary-data-analysis
   ```
2. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```
3. Launch Jupyter and open the notebook
   ```bash
   jupyter notebook Salary_Data_Analysis.ipynb
   ```

## Project Structure

```
salary-data-analysis/
├── Salary_Data_Analysis.ipynb
├── Salary_Dataset_DSL.csv
├── README.md
├── requirements.txt
└── .gitignore
```

## Notes

Salary figures reflect self-reported data and are influenced by sample size per company/role — findings on companies with few reports should be treated as indicative rather than statistically robust.
