# Blinkit Delivery Performance Analysis

## Project Overview

This project explores the decline in delivery performance at Blinkit as the business expands into new cities and neighbourhoods. The case study was assigned as part of the **NextLeap Data, Metrics and Outcomes Mapping** project.

The objective is to identify where delivery delays occur, define the metrics required to investigate them, and prioritise operational hypotheses that could improve delivery reliability and customer retention.

## Business Problem

Blinkit's delivery performance has deteriorated despite an increase in order volume.

Key business signals provided in the case study:

- On-time delivery rate declined from 93% to 85%.
- Average delivery time increased from 11 to 14 minutes.
- Late delivery complaints doubled.
- Goodwill credits increased by 60%.
- The five worst-performing cities on on-time delivery also have the lowest repeat order rates.

These signals suggest a need to investigate operational bottlenecks at the store, rider and last-mile delivery levels.

## Project Objectives

- Define the business objective and North Star Metric.
- Build a structured issue tree to investigate delivery delays.
- Map operational questions to measurable KPIs.
- Develop and prioritise hypotheses using impact, data availability and actionability.
- Identify opportunities to improve delivery performance and customer experience.

## North Star Metric

**On-Time Delivery Rate**

Formula:

On-Time Delivery Rate = (Orders delivered by the promised time / Eligible orders) × 100

The case study defines the delivery clock as starting when the customer places an order and stopping when the order is marked delivered. The delivery promise is frozen at checkout, with no grace period.

Blinkit-caused cancellations are treated as unsuccessful outcomes, while specified customer-side failures and scheduled orders are excluded from the eligible-order denominator.

## Issue Tree: Delivery Time Analysis

Delivery time is divided into four operational stages:

1. **Order Wait:** Time from order placement to the start of picking.
2. **Pick and Pack:** Time from picking start to order packing completion.
3. **Rider Pickup Lag:** Time from order packing to rider pickup.
4. **Last Mile:** Time from rider pickup to customer delivery.

Total delivery time = Order Wait + Pick and Pack + Rider Pickup Lag + Last Mile.

The analysis maps each stage to relevant metrics, including queue wait, picking time, orders per picker-hour, rider supply ratio, rider wait time, transit speed and weather-related delivery delays.

## Hypotheses and Prioritisation

The case study develops six hypotheses:

1. Rider availability drops during the 7 PM–10 PM peak.
2. A small proportion of stores account for a disproportionate share of late orders.
3. Riders lose significant time waiting at stores for orders to be packed.
4. A flat delivery promise fails to account for distance and demand conditions.
5. Customer complaints and goodwill credits increase sharply with the severity of delays.
6. Newer stores have longer picking times and higher late-delivery rates.

Each hypothesis is evaluated using a proposed test metric and explicit rejection criteria.

## Expected Business Impact

The proposed analysis aims to help Blinkit:

- Identify the operational stages contributing most to delivery delays.
- Prioritise high-impact stores and peak-hour bottlenecks.
- Improve rider utilisation and store handoff efficiency.
- Reduce severe delays, customer complaints and goodwill credits.
- Improve repeat ordering through more dependable delivery promises.

## Tools and Approach

- Business problem structuring
- KPI and metric definition
- Issue tree development
- Hypothesis-driven analysis
- Operational performance measurement
- Data-driven prioritisation

## Project Deliverable

The primary deliverable is a three-slide PDF covering the business objective, North Star Metric, operational issue tree, metric definitions and prioritised hypotheses.

**Note:** This repository documents the diagnostic framework and proposed analytical approach. The hypotheses require validation against the underlying order, store, rider, demand and customer datasets before conclusions can be drawn.

## Acknowledgement

Case study: NextLeap — Data, Metrics and Outcomes Mapping  
Business context: Blinkit delivery operations
