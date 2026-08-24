# Project Architecture

## End-to-End Analytics Architecture

The OEE Manufacturing Analytics solution follows an end-to-end data analytics architecture that transforms raw manufacturing ERP data into actionable business insights.

```text
Manufacturing ERP Data
        ↓
      MySQL
        ↓
   SQL Queries
        ↓
Data Transformation
        ↓
   Power BI Data Model
        ↓
    DAX Measures
        ↓
   OEE Calculations
        ↓
   Power BI Dashboard
        ↓
 Business Insights



 ---

## 1. Source Data

The analytics solution uses production data generated from a manufacturing ERP environment.

The source data contains information related to:

- Production
- Machines
- Shifts
- Production quantities
- Wastage
- Production time
- Make Ready time
- Non-productive time
- Production dates
- Departments

The data is stored in a MySQL database.

---

## 2. MySQL Database

MySQL acts as the primary data source for the analytics solution.

Production data is extracted from the ERP database using SQL queries.

The database provides the raw operational data required for manufacturing analysis.

---

## 3. SQL Data Transformation

SQL is used to prepare the raw ERP data before it is consumed by Power BI.

The transformation layer handles:

- Filtering relevant production records
- Aggregating production quantities
- Preparing machine-level data
- Preparing shift-level data
- Handling production and wastage information
- Calculating required analytical fields
- Reducing unnecessary data before loading into Power BI

This creates a structured dataset suitable for analytical reporting.

---

## 4. Power BI Data Model

The transformed data is loaded into Power BI and organized into an analytical data model.

The model supports analysis across multiple dimensions including:

- Date
- Machine
- Shift
- Department
- Production

The model was designed to support OEE, production efficiency and machine performance analysis.

---

## 5. DAX Calculation Layer

DAX is used to create business measures and analytical calculations inside Power BI.

Key calculations include:

- Availability
- Performance
- Quality
- OEE
- Actual Production
- Production Hours
- Production per Hour
- Production per Shift
- Wastage
- Make Ready Time
- Non-Productive Hours

The DAX layer converts the prepared production data into business KPIs.

---

## 6. OEE Calculation

Overall Equipment Effectiveness is calculated using the three fundamental OEE components:

```text
OEE = Availability × Performance × Quality
