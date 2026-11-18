# Blinkit Delivery Performance Analysis

A diagnostic framework and Power BI dashboard that investigates why quick-commerce orders are delivered late, built for the NextLeap *Data, Metrics and Outcomes Mapping* case study.

## Business problem

As Blinkit expanded into new cities, order volume grew but delivery reliability did not keep up. The case study reports:

- On-time delivery fell from 93% to 85%
- Average delivery time rose from 11 to 14 minutes
- Late-delivery complaints doubled and goodwill credits rose 60%
- The five worst cities on on-time delivery also have the lowest repeat-order rate

**Goal:** find where delivery time is spent, which parts Blinkit can control, and where a fix would have the biggest impact.

## North Star Metric

**On-Time Delivery Rate = (Orders delivered by the promised time ÷ Eligible orders) × 100**

- **Clock starts** when the customer places the order, and **stops** when the order is delivered.
- The promise is frozen at checkout, with no grace period.
- Blinkit-caused cancellations count as not on time. Customer-side failures and scheduled orders are excluded.

## Data

Four files in this repository (1,00,000 delivered orders, Jan to Jun 2026):

| File | Contents |
|---|---|
| `last_mile_deliveries.csv` | One row per order: distance, promised ETA, actual time, delay, weather, traffic, surge, rider experience, rating |
| `dark_store_locations.csv` | 36 dark stores: city, packing time, active riders, service radius |
| `ev_fleet_trips.csv` | EV trip details, linked to orders by `trip_id` |
| `quick_commerce_skus.csv` | Product catalogue with stock-out flags, linkable by city only |

## Issue tree

Delivery time is split into drivers that do not overlap:

- **Distance:** how far the order travels (order distance, store reach)
- **Riding speed:** road conditions (traffic, weather), demand load (peak hour, surge), rider and vehicle
- **Store fulfilment:** packing speed, rider capacity, item availability

Every branch has a metric, an equation and an analytical question. The full tree is in the PDF.

## Key findings

| # | Hypothesis | Result | Evidence |
|---|---|---|---|
| 1 | A flat promise ignores distance | **Supported** | The promise is 10, 12, 15 or 18 minutes in equal shares at every distance. A promise set by distance band lifts on-time delivery from **77.8% to 91.4%**, with a slightly lower average promise (13.4 vs 13.7 min) |
| 2 | Longer trips drive lateness | **Supported** | On-time is 100% under 1 km and about 10% above 4 km. Orders beyond 3 km are 19% of volume but 61% of late orders |
| 3 | Peak hours slow deliveries | **Supported** | On-time is 71.8% at peak vs 82.0% off-peak, and the gap holds at every distance |
| 4 | Traffic, weather and vehicle slow riders | **Supported** | On-time falls from 85% to 69% from light to heavy traffic, and to 55% in monsoon rain. ICE motorcycles reach 74% vs 80% for EV scooters |
| 5 | Ratings drop sharply only when badly late | **Partly** | Rating slides gradually from 4.86 (on time) to 3.77 (over 10 min late) |
| 6 | Slow stores or new riders cause delays | **Rejected** | Packing time, store differences and rider experience show no link to lateness |

Mumbai has the lowest on-time rate (74.4%), and it also has the heaviest traffic and slowest riders.

## Power BI dashboard

File: `blinkit.pbix` (open with Power BI Desktop).

- **Overview:** KPI cards, on-time % by month, by city and peak vs off-peak, with a city slicer
- **Drill-through:** right-click a city and drill through to **Delay Drivers** (distance, weather, hour, rider experience) or **Store Drill-down** (store table and scatter charts)
- **Tooltips:** hover over a city bar or a month for a quick breakdown
- **Promise What-if:** set the promised minutes for each distance band and see the new on-time rate


## Limitations

- The data shows a flat late rate of about 22% each month, so the 93% to 85% decline in the case brief is **not visible** in these files.
- There are no stage timestamps (picked, packed, rider arrival), complaint tickets, credits or hourly rider supply, so hypotheses that need them could not be tested.
- The what-if result is a simulation: it replays the same recorded delivery times against different promises, so it does not capture how customers would react.

## Repository contents

| File | Description |
|---|---|
| `Blinkit_Delivery_Metrics_Mapping.pdf` | Three-slide analysis: objective and North Star, issue tree, hypotheses |
| `blinkit.pbix` | Power BI dashboard |
| `*.csv` | Source data |
| `ML1_certificate.pdf` | Certificate of completion |

## Tools

Power BI, DAX, issue-tree structuring, hypothesis-driven analysis.

## Acknowledgement

Case study: NextLeap, *Data, Metrics and Outcomes Mapping*. Business context: Blinkit delivery operations.

## Certificate of Completion

Successfully completed the NextLeap Data, Metrics and Outcomes Mapping case study focused on Blinkit's delivery performance.

The project involved defining operational KPIs, structuring an issue tree, mapping metrics to business questions, and prioritising hypotheses to investigate delivery delays.

**Certificate:** [View Certificate](ML1_certificate.pdf)
