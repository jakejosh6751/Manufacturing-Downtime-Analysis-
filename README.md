# Manufacturing Downtime Analysis

## Executive Summary:
Using Power Query and Power BI, I analyzed soda bottling production line data and found that downtime caused a 36% inefficiency, extending batch duration by 23 hours. Operator errors were the leading drivers. Five factors–mainly machine adjustments, machine failure, and inventory shortage–accounted for 80% of total downtime. Base on these findings, I recommended targeted operator training, improved maintenance schedules, real-time inventory tracking, and upgrades to high-downtime equipment to boost operational efficiency.

### Business Problem:
For manufacturing companies, downtime directly impacts output and profitability. In this soda bottling plant, management noticed frequent production delays but lacked clear insights into the main causes. The goal was to analyze downtime data to identify key drivers and propose actionable strategies to reduce downtime.

### Methodology:
1. Extracted and cleaned downtime records from the production line excel file using Power Query.
2. Modelled data and performed detailed exploratory analysis using Power BI to quantify downtime distribution and identify critical drivers.
3. Visualised downtime data in Power BI to compare downtime contribution by operators, machine failure, and inventory shortages.

### Skills:
- Power Query: ETL, aggregation, unpivot.
- Power BI: Data modelling, DAX measures, calculated columns, interactive dashboard design.

## Insights & Recommendation:
**1. How does downtime impact production targets?**
![Insight 1.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis/blob/main/Insight%201.jpg)

> 36% downtime inefficiency extended batch duration by 23 hrs (1388 minutes) from a planned batch time of 41 hrs (2470 minutes).
- *Reduce downtime to meet delivery schedules and protect customer trust and sales.*

**2. What is the leading cause of downtime between operator and non-operator sources?**
![Insight 2.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis/blob/main/Insight%202.jpg)

> Operators were the leading cause of downtime.
- *Provide targeted operator training and clear standard operating procedures (SOPs) to reduce errors.*

**3. What drives downtime across operators?**
![Insight 3.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis/blob/main/Insight%203.jpg)

> Mac's downtime is mainly due to batch changes, while other operators struggle with machine adjustments.
- *Prioritize batch change training for Mac and machine adjustment training for other operators.*
  
**4. Which factors account for most of the downtime?**
![Insight 4.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis/blob/main/Insight%204.jpg)

> Five factors cause 80% of downtime; three are linked to operator errors.
- **Machine adjustment, Batch change, and Batch coding**: *Provide targeted training for operators.*
- **Machine Failure**: *Leverage preventive maintenance schedules to minimize or predict machine failure. Additionally, Upgrade or replace aging equipment with high downtime (need more data to ascertain age of equipment).*
- **Inventory Shortage**: *Implement real-time tracking systems or forecasting methods to maintain optimal stock levels.*

**5. How efficient are the operators overall?**
![Insight 5.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis/blob/main/Insight%205.jpg)

> Mac's efficiency is slightly below the overall average of all operators.
- *Provide Mac with focused coaching on batch changes to raise efficiency to peer level.*

## Additional Project Materials & Notes
- Power BI Report
![manufacturing downtime report.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis-/blob/main/manufacturing%20downtime%20report.jpg)

- Schema View
- Line downtime (Fact table) Transformation
- Line productivity (Fact table) Transformation
