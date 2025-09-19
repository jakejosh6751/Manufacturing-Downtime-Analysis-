# Manufacturing Downtime Analysis

## Executive Summary:
Using SQL, Python, and Power BI, I analyzed soda bottling production line data to identify the main causes of downtime. The analysis revealed that operator errors and batch changes account for most of the inefficiencies. Based on these findings, I recommend targeted operator training, improved maintenance schedules, and upgrades to high-downtime equipment to boost operational efficiency.

### Business Problem:
For manufacturing companies, downtime directly impacts output and profitability. In this soda bottling plant, management noticed frequent production delays but lacked clear insights into the main causes. The goal was to analyse downtime data to identify key drivers and propose actionable strategies to reduce downtime.

### Methodology:
1. Extracted and cleaned downtime records from the production line database using SQL.
2. Modelled and visualised downtime data in Power BI to compare operators, machines, and downtime causes.
3. Used Python (pandas, numpy, seaborn, matplotlib) for detailed statistical analysis to quantify downtime distribution and identify critical drivers.

### Skills:
- SQL: Joins, CTEs, CASE statements, filtering, grouping, aggregation
- Power BI: Data modelling, DAX measures, calculated columns, interactive dashboard design, ETL
- Python: pandas, numpy, matplotlib, seaborn, statistics, funnel-style root cause analysis

### Insights & Recommendation:



![manufacturing downtime report.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis-/blob/main/manufacturing%20downtime%20report.jpg)

Analyzed soda bottling production line data. Identified key causes of downtime, enabling targeted improvements in operational efficiency.

## Key Insights
1. Operators were the leading cause of dodowntime.
2. Mac's downtime is mainly due to batch changes, while other operators struggle with machine adjustments.
3. Five factors cause 80% of downtime; three are linked to operator errors.
4. Mac's efficiency is slightly below the overall average of all operators.

## Recommendation
1. Provide batch change training for Mac and machine adjustment training for other operators.
2. Leverage preventive maintenance schedules to minimize or predict machine failure.
3. Upgrade or replace aging equipment with high downtime (need more data to ascertain age of equipment).
4. Implement real-time tracking systems or forecasting methods to maintain optimal stock levels.

## Additional Project Files
- Data Dictionary
- 

