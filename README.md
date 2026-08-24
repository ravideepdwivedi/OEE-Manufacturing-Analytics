# OEE Manufacturing Analytics

## Real-World Manufacturing OEE Dashboard | Power BI + MySQL + SQL + DAX

A real-world Overall Equipment Effectiveness (OEE) analytics solution developed for a printing and packaging manufacturing environment.

This project transforms production data into actionable insights for monitoring machine performance, production efficiency, downtime, wastage and overall equipment effectiveness.

---

## Project Overview

The objective of this project is to build a manufacturing analytics solution that helps management and production teams monitor:

- Overall Equipment Effectiveness (OEE)
- Availability
- Performance
- Quality
- Production Quantity
- Wastage
- Machine Performance
- Production Hours
- Make Ready (MR) Time
- Non-Productive Hours
- Production per Hour
- Production per Shift
- Department-wise Production
- Day-wise OEE

---

## Technology Stack

| Technology | Purpose |
|---|---|
| Power BI | Dashboard and Data Visualization |
| DAX | OEE calculations and analytical measures |
| MySQL | Production database |
| SQL | Data extraction and transformation |
| Power Query | Data preparation |
| Excel | Data validation and supporting analysis |

---

## OEE Framework

The project follows the standard OEE methodology:

### OEE = Availability × Performance × Quality

### Availability

Measures how effectively available production time is utilized.

### Performance

Measures actual production against planned production capacity.

### Quality

Measures good production against total production including wastage.

---

## Dashboard Features

### 1. OEE Dashboard

The main dashboard provides a high-level view of manufacturing performance.

![OEE Dashboard](DASHBOARD%20WITHOUT%20BLANK%20FEATURE.jpeg)

### 2. Day-wise OEE Analysis

Tracks OEE performance across production dates.

![Day Wise OEE](DAY%20WISE%20OEE.jpeg)

### 3. Department-wise Production

Provides department-level production analysis.

![Department Wise Production](DEPARTMENT%20WISE%20ACTUAL%20PRODUCTION.jpeg)

### 4. OEE Dashboard Analysis

Additional dashboard view showing detailed production and OEE analysis.

![OEE Dashboard Analysis](DAY%20WISE%20OEE%20PART%20-%202.jpeg)

---

## Key KPIs

The Power BI solution includes measures for:

- OEE %
- Availability %
- Performance %
- Quality %
- Production Quantity
- Good Quantity
- Wastage Quantity
- Actual Run Time
- Productive Hours
- Make Ready Hours
- Non-Productive Hours
- Average Make Ready Time
- Average Production per Hour
- Production per Shift
- Available Shifts
- Planned Production Quantity

---

## Data Model

The Power BI data model was designed around production, machine, shift and operational data.

Detailed documentation is available here:

[View Data Model](Data_Model.md)

---

## SQL Data Extraction

Production data is extracted from MySQL using SQL queries.

The SQL layer includes production, machine, shift, order and operational information required for OEE analysis.

[View SQL Queries](SQL_Queries.md)

---

## DAX Measures

The Power BI analytical layer contains custom DAX measures for calculating OEE components, production KPIs, availability, performance, quality and loss analysis.

[View DAX Measures](DAX_Measures.md)

---

## Manufacturing Analytics Workflow

```text
MySQL Production Database
          ↓
     SQL Queries
          ↓
    Data Preparation
          ↓
       Power BI
          ↓
      DAX Measures
          ↓
   OEE Calculations
          ↓
Manufacturing Dashboard
          ↓
Management Insights
