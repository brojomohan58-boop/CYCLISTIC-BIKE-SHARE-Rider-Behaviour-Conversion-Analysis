# 📖 Data Dictionary

## Cyclistic Bike-Share 2025 — Column Reference

This dictionary covers all columns in the cleaned dataset
(`cyclistic_2025_cleaned`) and the Tableau export table
(`cyclistic_dashboard_final`).

---

## Original Columns (from raw Divvy data)

| Column | Type | Example | Description |
|---|---|---|---|
| `ride_id` | STRING | `ABC123XYZ` | Unique identifier for each ride |
| `rideable_type` | STRING | `classic_bike` | Bike type: `classic_bike` or `electric_bike` |
| `started_at` | TIMESTAMP | `2025-06-14 08:23:11` | Ride start datetime (UTC) |
| `ended_at` | TIMESTAMP | `2025-06-14 08:41:44` | Ride end datetime (UTC) |
| `start_station_name` | STRING | `Shedd Aquarium` | Name of the starting docking station |
| `end_station_name` | STRING | `Navy Pier` | Name of the ending docking station |
| `start_lat` | FLOAT | `41.8672` | Latitude of start station |
| `start_lng` | FLOAT | `-87.6154` | Longitude of start station |
| `end_lat` | FLOAT | `41.8923` | Latitude of end station |
| `end_lng` | FLOAT | `-87.6120` | Longitude of end station |
| `member_casual` | STRING | `casual` | Rider type: `member` (annual) or `casual` (single/day pass) |

---

## Calculated Columns (added in transformation step)

| Column | Type | Example | Description | Formula |
|---|---|---|---|---|
| `ride_duration` | INTEGER | `18` | Ride length in minutes | `TIMESTAMP_DIFF(ended_at, started_at, MINUTE)` |
| `hour_of_day` | INTEGER | `8` | Hour when ride started (0–23) | `EXTRACT(HOUR FROM started_at)` |
| `month_num` | INTEGER | `6` | Month number (1–12) | `EXTRACT(MONTH FROM started_at)` |
| `month_name` | STRING | `June` | Full month name | `FORMAT_TIMESTAMP('%B', started_at)` |
| `day_of_week` | STRING | `Saturday` | Full day name | `FORMAT_TIMESTAMP('%A', started_at)` |
| `day_type` | STRING | `Weekend` | `Weekday` (Mon–Fri) or `Weekend` (Sat–Sun) | CASE on `day_of_week` |
| `season` | STRING | `Summer` | `Winter`, `Spring`, `Summer`, or `Autumn` | CASE on `month_num` |
| `trip_type` | STRING | `Round Trip` | `Round Trip` if start = end station, else `One Way` | CASE on station names |
| `distance_miles` | FLOAT | `1.34` | Straight-line distance between start and end (miles) | `ST_DISTANCE` geospatial / 1000 × 0.621371 |
| `duration_bucket` | STRING | `11–20 min` | Grouped duration range | CASE on `ride_duration` |
| `time_segment` | STRING | `Morning (6–9am)` | Named time window | CASE on `hour_of_day` |

---

## Derived / Joined Columns (in dashboard export only)

| Column | Type | Example | Description |
|---|---|---|---|
| `casual_pct` | FLOAT | `82.19` | % of rides at this station that are casual riders |
| `conversion_priority_score` | FLOAT | `75.1` | Composite score (0–100) rating each station's conversion potential |

### Conversion Priority Score Formula

```
score = (casual_pct_at_station × 0.40)
      + (normalized_volume × 0.40)      -- volume / 40,000 cap
      + (commute_hour_casual_share × 0.20)
```

Higher score = better station target for membership conversion campaigns.

---

## Category Value Reference

### `rideable_type`
| Value | Description |
|---|---|
| `classic_bike` | Non-motorized standard bicycle |
| `electric_bike` | Pedal-assist electric bicycle |

### `member_casual`
| Value | Description |
|---|---|
| `member` | Annual membership holder |
| `casual` | Single-ride or day-pass purchaser |

### `season`
| Value | Months |
|---|---|
| `Winter` | December, January, February |
| `Spring` | March, April, May |
| `Summer` | June, July, August |
| `Autumn` | September, October, November |

### `duration_bucket`
| Value | Range |
|---|---|
| `0–10 min` | 1 to 10 minutes |
| `11–20 min` | 11 to 20 minutes |
| `21–40 min` | 21 to 40 minutes |
| `40+ min` | 41 minutes and above |

### `time_segment`
| Value | Hours |
|---|---|
| `Morning (6–9am)` | 06:00 – 09:59 |
| `Midday (10am–2pm)` | 10:00 – 14:59 |
| `Afternoon (3–6pm)` | 15:00 – 18:59 |
| `Evening (7–10pm)` | 19:00 – 22:59 |
| `Night (11pm–5am)` | 23:00 – 05:59 |

### `trip_type`
| Value | Condition |
|---|---|
| `Round Trip` | `start_station_name = end_station_name` (both non-NULL) |
| `One Way` | Start and end stations are different |
