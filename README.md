# 🚴 Cyclistic Bike-Share: Rider Conversion Analysis
 
![BigQuery](badge-bigquery) ![Python](badge-python) ![Tableau](badge-tableau)
 
## 📋 Project Overview
End-to-end data analysis of **5.4M bike-share rides** to identify
behavioral differences between casual riders and annual members,
with actionable recommendations to increase membership conversion.
 
**Business Question:** How do annual members and casual riders use
Cyclistic bikes differently — and how can marketing convert casuals?
 
## 🛠 Tools & Technologies
| Tool | Purpose |
| Google BigQuery | Data cleaning, transformation, analysis (SQL) |
| Python / Google Colab | Statistical analysis, hypothesis testing |
| Tableau Desktop | 3-dashboard interactive visualization |
 
## 📊 Key Findings
- Members ride **1.7× shorter** on average (11.6 min vs 19.5 min)
  — statistically proven: Welch's T-test p < 0.001, Cohen's d = -0.26
- Members peak at **8am & 5pm** (commuters); casuals build from midday
- Casual ridership drops **93% from August to December**
- Casual riders take **3.7× more round trips** → strong leisure signal
 
## 📁 Repository Structure
01_data/          → Data documentation and sample (no large CSVs)
02_sql/           → 6 BigQuery SQL scripts (combine, transform, clean, analyze)
03_python/        → Colab notebook + 8 analysis charts
04_dashboards/    → Tableau workbook + 3 dashboard screenshots
05_docs/          → Case study report and key findings
 
## 🔗 Live Dashboard
👉 [View on Tableau Public](https://public.tableau.com/views/CyclisticRiderBehaviorMembershipConversionAnalysis/ExecutiveOverview?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
 
## 🏆 Top 3 Recommendations
1. **Station kiosks** at top 5 tourist corridor stations (57–82% casual)
2. **Weekend midday campaigns** — Sat/Sun 10am–2pm peak (148K casual rides)
3. **Target 11–20 min casual riders** — 27.5% of casuals, most convertible
 
## 📜 Data Source
Divvy trip data (Motivate International Inc.) — public license.
Download: https://divvy-tripdata.s3.amazonaws.com/index.html
Processed in: Google BigQuery (project: model-myth-487516-u3)
