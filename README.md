# OEE Manufacturing Analytics

## Real-World Manufacturing OEE Dashboard | Power BI + MySQL + SQL + DAX

A real-world Overall Equipment Effectiveness (OEE) analytics solution developed for a printing and packaging manufacturing environment.

This project was built single-handedly to transform complex ERP and manufacturing data into a dynamic analytical solution for monitoring machine performance, production efficiency and quality.

---

## Project Overview

This project focuses on developing a dynamic OEE monitoring and manufacturing performance analytics solution using:

- Power BI
- DAX
- MySQL
- SQL
- ERP Data
- Manufacturing Analytics

The dashboard provides a consolidated view of manufacturing performance and allows analysis across machines, shifts, dates, operators and materials.

The solution is connected to ERP data through MySQL and uses SQL queries for data extraction and DAX for dynamic business calculations.

---

## Business Problem

Before this solution was developed, the organization did not have a consolidated OEE dashboard for dynamically analysing production performance, machine efficiency and quality.

Manufacturing data was available through the ERP, but extracting meaningful analytical insights required understanding a large and complex database structure.

The objective was to convert this complex operational data into a practical management analytics solution.

---

## Why This Project Was Challenging

The ERP database contains 520+ tables with highly interconnected and complex manufacturing data.

The major challenge was not simply creating Power BI charts.

The project required:

- Understanding the ERP database structure
- Identifying relevant data sources
- Reverse-engineering required information across different areas
- Developing SQL queries for data extraction
- Understanding printing and packaging manufacturing processes
- Translating manufacturing business logic into DAX
- Creating dynamic KPI calculations
- Handling machine-specific production logic
- Analysing shift-level production performance
- Connecting multiple operational dimensions
- Designing a management-oriented analytical dashboard

This required understanding both the technology and the manufacturing business process behind the data.

---

## Manufacturing Environment

The solution is designed for a large-scale printing and packaging manufacturing environment.

The manufacturing setup includes 143 machines, including advanced technology-based machines sourced internationally.

Some of these machines represent significant capital investments, with individual machine investments reaching approximately ₹15–25 crore.

Monitoring the performance of such assets requires visibility into:

- Availability
- Performance
- Quality
- Production
- Wastage
- Machine utilization
- Shift performance

The OEE framework provides a structured way to analyse these factors.

---

## OEE Metrics

The dashboard evaluates the three primary components of OEE:

### Availability

Measures how effectively available production time is utilized.

### Performance

Measures production performance against the expected/rated production capability of the selected machine and production context.

### Quality

Evaluates good production in relation to total production, considering production quality and wastage.

### Overall Equipment Effectiveness

OEE combines:

**Availability × Performance × Quality**

The calculations are implemented using DAX and dynamically respond to the selected analytical context.

---

## Dynamic Analysis

The dashboard allows users to analyse manufacturing performance across multiple dimensions, including:

- Machine
- Shift
- Date
- Operator
- Material
- Production
- Wastage

Changing the selected filters dynamically recalculates the relevant KPIs and visualizations.

---

## Data Flow

```text
ERP
  ↓
MySQL Database
  ↓
SQL Queries
  ↓
Data Preparation
  ↓
Power BI Data Model
  ↓
DAX Business Logic
  ↓
OEE Calculations
  ↓
Interactive Dashboard
  ↓
Manufacturing Insights
