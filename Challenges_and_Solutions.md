# Challenges & Solutions

## Real-World Manufacturing Analytics Challenges

This project was developed using real-world manufacturing production data from a printing and packaging environment. During the development of the OEE analytics solution, several data, calculation and reporting challenges were addressed.

---

## 1. Complex ERP Production Data

### Challenge

The production data was generated from an ERP system containing multiple production records, machine information, shift details and operational fields.

The raw data was not directly structured for analytical reporting.

### Solution

SQL queries were used to extract, transform and prepare the required production data before connecting it to Power BI.

This created a cleaner analytical dataset for OEE and production reporting.

---

## 2. Production Data Duplication

### Challenge

Production records could contain multiple entries for the same production activity, which could lead to incorrect production totals.

### Solution

SQL transformations and aggregation logic were applied to correctly consolidate production records and avoid misleading production calculations.

---

## 3. Machine-Level Production Analysis

### Challenge

Management required visibility into individual machine performance rather than only overall production.

### Solution

Machine-level production metrics were developed to analyse:

- Actual Production
- Production Hours
- Production per Hour
- Production per Shift
- Machine Performance
- Wastage
- OEE

This allowed underperforming machines to be identified more easily.

---

## 4. OEE Calculation

### Challenge

Overall Equipment Effectiveness requires the combination of Availability, Performance and Quality.

Calculating these metrics from raw production data required consistent business logic.

### Solution

Power BI DAX measures were created to calculate:

**OEE = Availability × Performance × Quality**

The calculations were designed to support machine, shift, department and date-level analysis.

---

## 5. Availability Analysis

### Challenge

Available production time needed to be compared with actual productive time.

Different shifts and machine conditions made simple time calculations insufficient.

### Solution

Availability was calculated using production availability and operating time, allowing management to identify capacity losses and machine utilization issues.

---

## 6. Make Ready and Non-Productive Time

### Challenge

Not all machine time contributes directly to production.

Make Ready time and other non-productive periods can significantly affect manufacturing efficiency.

### Solution

Make Ready and Non-Productive Hours were separately incorporated into the analytical model.

This provided better visibility into where available production time was being lost.

---

## 7. Wastage and Quality Analysis

### Challenge

Production quantity alone does not represent manufacturing efficiency.

Wastage and rejected quantities can significantly affect the quality component of OEE.

### Solution

Production and wastage metrics were analysed together to provide a clearer view of:

- Good Production
- Wastage
- Quality Performance
- Production Efficiency

---

## 8. Shift-Wise Performance

### Challenge

Production performance can vary significantly between shifts.

Overall daily production numbers may hide these differences.

### Solution

Shift-level analysis was implemented to compare production performance across different shifts.

This helps identify variations in:

- Production quantity
- Production efficiency
- Machine utilization
- OEE

---

## 9. Department-Level Analysis

### Challenge

Management also required visibility into production performance across departments.

### Solution

Department-wise production analysis was incorporated into the dashboard to identify:

- Production contribution
- Efficiency differences
- Bottlenecks
- Areas requiring improvement

---

## 10. SQL Performance and Data Extraction

### Challenge

Manufacturing databases can contain large production datasets, making complex SQL queries expensive to execute.

### Solution

SQL queries were structured to filter relevant records, aggregate production data and retrieve only the required analytical fields.

This helped improve data extraction efficiency and supported Power BI reporting.

---

## 11. Dynamic Power BI Analysis

### Challenge

Management required the ability to analyse production performance across different dates, machines, shifts and departments.

### Solution

The Power BI model and DAX measures were designed to support dynamic filtering and interactive analysis.

Users can analyse manufacturing performance from multiple business perspectives without manually preparing separate reports.

---

## 12. From Raw Data to Business Insights

### Challenge

Raw production data contains information, but management needs actionable insights rather than only numbers.

### Solution

The final solution converts production data into business-oriented metrics and visualizations.

The dashboard helps identify:

- Machine performance issues
- Production bottlenecks
- Downtime and capacity losses
- Wastage
- Shift-level variations
- Department-level performance
- Overall OEE performance

---

## Business Impact

The solution provides a centralized analytical view of manufacturing performance.

It supports management and production teams in:

- Monitoring machine performance
- Identifying production bottlenecks
- Improving equipment utilization
- Reducing non-productive time
- Monitoring wastage
- Comparing shift performance
- Supporting data-driven operational decisions

---

## Technology Used

- Power BI
- DAX
- MySQL
- SQL
- Advanced Excel
- Manufacturing ERP Data
- Data Analytics

---

## Overall Outcome

The project demonstrates how raw manufacturing ERP data can be transformed into a structured OEE analytics solution using SQL, Power BI and DAX.

The focus was not only on dashboard development, but also on solving real-world manufacturing data and analytical challenges.
