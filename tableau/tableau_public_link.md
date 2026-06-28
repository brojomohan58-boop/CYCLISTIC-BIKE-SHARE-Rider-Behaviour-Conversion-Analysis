# 📊 Tableau Public Dashboard

## Live Interactive Dashboard

🔗 **[View on Tableau Public](YOUR_TABLEAU_PUBLIC_URL_HERE)**

> Replace `YOUR_TABLEAU_PUBLIC_URL_HERE` with your actual published link.
> Example format: `https://public.tableau.com/app/profile/yourname/viz/CyclisticRiderBehaviorConversionAnalysis/ExecutiveOverview`

---

## Dashboard Overview

**Project:** Cyclistic Rider Behavior & Conversion Analysis 2025  
**Tool:** Tableau Desktop → Published to Tableau Public  
**Data:** 5,399,796 rides · January–December 2025

---

## Three-Dashboard Story

### Dashboard 1 — Executive Overview
*"What is happening?"*

Gives executives the business story in under 30 seconds.

| Visual | Insight |
|---|---|
| KPI Strip (4 tiles) | 5.4M rides · 14 min avg · 35.5% casual · Summer peak |
| Rider Composition Donut | 65% member / 35% casual split with volume table |
| Monthly Ride Trend | Seasonal bands showing casual 93% winter drop |
| Weekly Ride Pattern | Member weekday dominance vs casual weekend surge |
| Chicago Ride Density Map | Casual cluster on lakefront, members spread citywide |

---

### Dashboard 2 — Rider Behavioural Pattern
*"Why are they different?"*

Shows the analytical evidence behind the behavioral split.

| Visual | Insight |
|---|---|
| Ride Duration Distribution | Members cluster 0–10 min; casuals spread to 40+ min |
| Duration Bucket Breakdown | 62% of member rides < 10 min vs 46% for casual |
| Hourly Ride Pattern | Member 8am + 5pm commute peaks vs casual midday build |
| Round Trip vs One-Way | Casual round trip rate 3.74× higher than members |
| Bike Type Usage | Casual classic bike avg 28.65 min — largest gap |
| Weekday vs Weekend Rides | Members 76.6% weekday; casual 37.2% weekend |
| Avg Ride Duration | Casual weekend avg 22 min vs member 12.86 min |

---

### Dashboard 3 — Conversion Opportunity
*"Where and when to act?"*

Turns analysis into specific, actionable marketing recommendations.

| Visual | Insight |
|---|---|
| Casual Rider Concentration Map | Red dots = high casual % stations along lakefront |
| Top 10 Conversion Priority Stations | DuSable Lake Shore Dr (75.1) leads the ranking |
| Conversion Opportunity Matrix | Quadrant plot: high casual % + high volume = Priority Targets |
| Best Campaign Windows Heatmap | Saturday midday (148K) and Sunday midday (123K) peak |

---

## Tableau Workbook

The `.twb` workbook file is included in this folder as `Cyclistic_dashboard.twb`.

To open locally:
1. Download the workbook file
2. Open in Tableau Desktop (version 2024.1 or later recommended)
3. Reconnect to your own CSV data source when prompted

---

## Technical Notes

- **Color scheme:** Member = `#E6820E` (orange) · Casual = `#6A73C1` (blue-purple)
- **Map provider:** Mapbox via Tableau built-in
- **Navigation:** Tab-based navigation between all 3 dashboards
- **Interactivity:** Dashboard 3 includes station-level filter action (click map → filters all charts)
- **Data source:** `cyclistic_dashboard_final` exported from BigQuery as CSV
