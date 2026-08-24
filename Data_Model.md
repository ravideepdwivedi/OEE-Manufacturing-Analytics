# Data Model

## Power BI Data Model

The Power BI data model was designed to support OEE, production performance, machine analysis, availability, performance and quality monitoring.

![Power BI Data Model](./DATA_MODEL.png)

## Key Components

- Production Data
- Machine Information
- Shift Information
- Production Quantity
- Wastage Quantity
- Production Hours
- Make Ready Hours
- Rated Machine Speed
- Availability
- Performance
- Quality
- OEE Calculations

## Analytical Flow

ERP Data  
↓  
MySQL Database  
↓  
SQL Data Preparation  
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
