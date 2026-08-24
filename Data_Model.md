# Data Model

## Power BI Data Model

The Power BI data model was designed to support OEE, production performance, machine analysis, availability, performance and quality monitoring.

<img width="1600" height="844" alt="DATA_MODEL" src="https://github.com/user-attachments/assets/727715d5-c1aa-4105-beee-741935ec1de2" />

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
