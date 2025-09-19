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

### Insights & Recommendation
**1. What is the leading cause of downtime between operator and non-operator sources?**
> Operators were the leading cause of downtime.
- *Provide targeted operator training and clear standard operating procedures (SOPs) to reduce errors.*

**2. What drives downtime across operators?**
> Mac's downtime is mainly due to batch changes, while other operators struggle with machine adjustments.
- *Prioritize batch change training for Mac and machine adjustment training for other operators.*
  
**3. Which factors account for most of the downtime?**
> Five factors cause 80% of downtime; three are linked to operator errors.
- **Machine adjustment, Batch change, and Batch coding**: *Provide targeted training for operators.*
- **Machine Failure**: *Leverage preventive maintenance schedules to minimize or predict machine failure.*
- **Inventory Shortage**: *Implement real-time tracking systems or forecasting methods to maintain optimal stock levels.*

**4. How efficient are the operators overall?**
> Mac's efficiency is slightly below the overall average of all operators.
- *Provide Mac with focused coaching on batch changes to raise efficiency to peer level.*

### What actions can reduce downtime and improve efficiency?
- Training, preventive maintenance, equipment upgrades, and real-time tracking.

  Upgrade or replace aging equipment with high downtime (need more data to ascertain age of equipment).

## Additional Project Materials
- Power BI Report
![manufacturing downtime report.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis-/blob/main/manufacturing%20downtime%20report.jpg)

- Data Dictionary
- Metrics Dictionary

