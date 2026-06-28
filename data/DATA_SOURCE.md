# 📦 Data Source Documentation

## Overview

This project analyzes **5,399,796 bike-share rides** from Chicago's
Divvy bike-share system (January–December 2025) to identify behavioral
differences between casual riders and annual members.

---

## Raw Data

| Field | Detail |
|---|---|
| **Source** | Divvy Bike-Share Trip Data |
| **Provider** | Motivate International Inc. |
| **License** | Public — [Divvy Data License Agreement](https://divvybikes.com/data-license-agreement) |
| **Period** | January 2025 – December 2025 (12 monthly CSV files) |
| **Download** | https://divvy-tripdata.s3.amazonaws.com/index.html |
| **Original size** | ~1.2 GB uncompressed across 12 files |
| **Format** | CSV — one row per individual ride |

---

## Why CSVs Are Not in This Repository

Raw monthly CSVs exceed GitHub's 100 MB per-file limit.  
The cleaned/transformed dataset is **1.14 GB** — far too large for GitHub hosting.

To reproduce this analysis:
1. Download the 12 monthly CSV files from the link above (filenames: `202501-divvy-tripdata.csv` through `202512-divvy-tripdata.csv`)
2. Upload each file to Google BigQuery as `cyclistic_2025_01` through `cyclistic_2025_12` in a dataset called `cyclistic_analysis`
3. Run the SQL scripts in `02_sql/` in numbered order

---

## BigQuery Pipeline

All processing was done in **Google BigQuery** (project: `model-myth-487516-u3`).

| Table | Rows | Description |
|---|---|---|
| `cyclistic_2025_raw` | 5,549,796 | 12 months combined via UNION ALL |
| `cyclistic_2025_transformed` | 5,549,796 | Adds 8 calculated columns (duration, season, trip_type, etc.) |
| `cyclistic_2025_cleaned` | **5,399,796** | After quality filters applied |
| `cyclistic_dashboard_final` | 5,399,796 | Optimized export for Tableau (~350 MB) |
| `cyclistic_python_sample` | ~107,000 | 2% TABLESAMPLE for Python statistical analysis |

---

## Data Cleaning Summary

| Issue | Action | Rows Removed |
|---|---|---|
| Ride duration < 1 minute | Removed (false starts / re-docks) | ~45,000 |
| Ride duration > 1,440 minutes (24 hrs) | Removed (lost or stolen bikes) | ~800 |
| NULL coordinates (lat/lng) | Removed (needed for map visualizations) | ~95,000 |
| NULL `member_casual` field | Removed | < 100 |
| Duplicate `ride_id` values | Kept first occurrence only | ~4,100 |
| Year outliers (non-2025 timestamps) | Removed | ~200 |

**Final clean dataset: 5,399,796 rides** (97.3% retention rate)

---

## Validation Results (Post-Cleaning)

```
total_rows  min_dur  max_dur  avg_dur  null_type  null_dur  null_lat
5,399,796      1       1,439   14.41       0          0         0
```

---

## Privacy & Ethics

- Dataset contains **no personally identifiable information (PII)**
- Rider identities are anonymized by the data provider
- No credit card or personal data is present
- Data is used strictly for analytical and educational purposes

---

## Sample Data

A 1,000-row sample is included in this folder as `sample_data.csv`
to allow inspection of the data structure without downloading the full dataset.
