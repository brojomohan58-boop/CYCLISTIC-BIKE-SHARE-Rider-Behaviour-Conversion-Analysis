# 🔍 Key Findings — Cyclistic Bike-Share 2025

**Business Question:** How do annual members and casual riders use Cyclistic bikes differently?  
**Dataset:** 5,399,796 rides · January–December 2025 · Chicago, IL  
**Tools:** BigQuery SQL · Python (scipy) · Tableau Desktop

---

## Dataset Summary

| Metric | Value |
|---|---|
| Total rides (cleaned) | 5,399,796 |
| Annual members | 3,484,147 (64.5%) |
| Casual riders | 1,915,649 (35.5%) |
| Analysis period | Jan 2025 – Dec 2025 |
| Stations with data | 1,865 |

---

## Finding 1 — Ride Duration: Casual Riders Ride 1.7× Longer

| Metric | Member | Casual | Gap |
|---|---|---|---|
| Mean duration | 11.68 min | 19.37 min | +66% |
| Median duration | 8 min | 11 min | +38% |
| 0–10 min share | 61.8% | 46.4% | Members shorter |
| 40+ min share | 2.1% | 9.5% | Casual longer |

**Statistical proof:** Welch's T-test p < 0.001 · Cohen's d = −0.26 · Mann-Whitney p < 0.001  
**Interpretation:** The duration gap is statistically significant across all three tests. Casual riders explore; members commute.

---

## Finding 2 — Time Patterns: Two Completely Different Rhythms

**Members (commuter pattern):**
- Peak at **08:00** (252,029 rides) and **17:00** (375,145 rides)
- 76.6% of rides on weekdays
- Consistent volume Mon–Thu (493K–565K rides/day)

**Casual riders (leisure pattern):**
- Gradual build from midday, single peak around **15:00–17:00**
- 37.2% of rides on weekends (Sat + Sun)
- Saturday avg duration 21.81 min — highest of any day

---

## Finding 3 — Seasonal Concentration

| Season | Casual Rides | % of Casual Total | Member Rides | % of Member Total |
|---|---|---|---|---|
| Winter | 77,482 | 4.0% | 343,792 | 9.9% |
| Spring | 363,764 | 19.0% | 780,370 | 22.4% |
| Summer | 910,627 | 47.5% | 1,253,034 | 36.0% |
| Autumn | 563,776 | 29.4% | 1,106,951 | 31.8% |

**Key insight:** Casual ridership drops 93% from August (323,523) to January (23,405).  
Members drop only 75% — far more resilient in winter.  
**Conversion window:** Spring (Mar–May) — casual ridership growing but not yet at peak.

---

## Finding 4 — Round Trip Behavior Proves Leisure Use

| Metric | Member | Casual |
|---|---|---|
| Round trip rate | 1.49% | 5.57% |
| Round trip avg duration | 23.38 min | 38.70 min |
| Top round trip routes | University of Chicago commuter loop | DuSable Lake Shore, Navy Pier, Millennium Park |

**Casual riders take round trips 3.74× more often** — looping back to the same tourist station.  
Member top routes are sub-5-minute point-to-point commuter shuttles.

---

## Finding 5 — Bike Type Gap Largest on Classic Bikes

| Bike Type | Member Avg | Casual Avg | Gap |
|---|---|---|---|
| Classic bike | 13.11 min | 28.65 min | 2.19× |
| Electric bike | 10.85 min | 14.40 min | 1.33× |

**Casual riders choose classic bikes for longer leisure rides.**  
Electric bikes reduce the gap — possibly because speed limits the exploration advantage.

---

## Finding 6 — Distance Is Nearly Identical

| Metric | Member | Casual |
|---|---|---|
| Avg distance | 1.41 miles | 1.39 miles |
| T-test p-value | 0.0306 | (statistically significant but practically negligible) |

**The behavioral difference is in TIME, not DISTANCE.**  
Both groups cover similar distances but casual riders take much longer to do it — confirming slow, exploratory leisure riding.

---

## Finding 7 — Top Conversion Target Stations

| Rank | Station | Casual % | Priority Score |
|---|---|---|---|
| 1 | DuSable Lake Shore Dr & Monroe St | 78.97% | 75.1 |
| 2 | Navy Pier | 78.00% | 70.3 |
| 3 | Streeter Dr & Grand Ave | 78.74% | 66.1 |
| 4 | Millennium Park | 69.36% | 59.4 |
| 5 | Shedd Aquarium | 82.19% | 57.3 |

All top stations are Chicago tourist corridor locations along the lakefront.

---

## Finding 8 — Best Campaign Timing Windows

| Time Window | Casual Rides | Notes |
|---|---|---|
| Saturday Midday (10am–2pm) | 148,000 | Highest casual volume of any window |
| Sunday Midday (10am–2pm) | 123,000 | Second highest |
| Saturday Afternoon (3–6pm) | 120,000 | Strong secondary window |
| Friday Afternoon (3–6pm) | 110,000 | Best weekday window |

---

## Top 3 Recommendations

### 1. 🎯 Station-Level Kiosk Campaign
Deploy membership sign-up kiosks and QR-code promotions at the top 5 tourist corridor stations (DuSable Lake Shore Dr, Navy Pier, Streeter Dr, Millennium Park, Shedd Aquarium). These stations have 57–82% casual ridership and account for over 120,000 casual rides per month at peak.

### 2. 📅 Weekend Midday Digital Campaign
Launch geo-targeted digital ads and push notifications on Saturday and Sunday between 10am and 2pm — the highest-volume casual riding windows (148K and 123K rides respectively). Begin the campaign in March–April before the summer surge when casual riders are returning to the platform.

### 3. 💰 Target the 11–20 Minute Casual Segment
Focus conversion messaging on the 527,338 casual riders (27.5% of all casual rides) who take 11–20 minute trips. This segment rides long enough to recognize the value of membership but short enough to suggest regular, potentially habitual use. Show cost comparison: repeated single passes vs annual membership.

---

## Statistical Validation Summary

| Test | Result | Interpretation |
|---|---|---|
| Welch's T-test | p < 0.001 | Rejects H0 — duration gap is real |
| Mann-Whitney U | p < 0.001 | Non-parametric confirmation |
| Cohen's d | −0.26 (small) | Consistent, measurable effect |
| Distance T-test | p = 0.031 | Statistically sig. but negligible (0.02 mi gap) |

---

*Data: Divvy/Cyclistic 2025 · Motivate International Inc. · Public license*  
*Analysis: Google BigQuery SQL + Python/Google Colab + Tableau Desktop*
