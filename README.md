# Manufacturing Downtime Analysis in Soda Bottling
___

## Project Overview
Downtime in manufacturing refers to periods when production is halted, impacting efficiency, productivity, and profitability. It can stem from equipment failure, maintenance, operator, or supply chain issues, leading to significant operational costs.

Analyzing downtime is crucial for identifying root causes, minimizing disruptions, and optimizing workflows. By addressing downtime effectively, companies can achieve higher production reliability and cost savings.

## Key Objectives
- Identify the root causes of downtime.
- Propose actionable solutions to reduce downtime.
- Optimize operational efficiency in manufacturing.

## Key Insights

![Manufacturing Downtime_1.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis-/blob/main/manufacturing%20downtime_1.jpg)

## Report Summary
![Manufacturing Downtime_2.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis-/blob/main/manufacturing%20downtime_2.jpg)

## Techniques & Procedures

## Project Fles






### 2.3 Data Cleaning
* "Downtime factors" table
  - Changed column name 'Factor' to 'Downtime Factor'
* "Line downtime" table
  - Removed first row: has only one column title (Downtime factor) representing multiple parameters.
  - Promoted first row to headers.
  - Replaced null values in column '1' with 0. This is to ensure the downtime description 'Emergency stop' represented by 1 appears in visuals.
  - Unpivoted other columns except 'Batch'.
  - Renamed columns 'Attribute' to 'Downtime Factor', 'Value' to 'Downtime', and changed data types.

### 2.4 Data Modeling
| 'Table'[Feature] 1 | 'Table'[Feature] 2 | Cardinality |
|-|-|-|
| 'Line productivity'[Batch] | 'Line downtime'[Batch] | One-to-One |
| 'Products'[Product] | 'Line productivity'[Product] | One-to-Many |
| 'Downtime factors'[Downtime Factor] | 'Line downtime'[Downtime Factor] | One-to-Many |


### 2.5 Data Transformation
- Calculated Columns

| Table | Calculated Column | Expression |
|-|-|-|
| Line downtime | Description | RELATED('Downtime factors'[Description]) |
| | Operator error | RELATED('Downtime factors'[Operator Error]) |
| | | |
| Line productivity | Actual Batch Time | IF(INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)<0, INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)+1440, INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)) |
| | Minimum Batch Time | RELATED(Products[Min batch time]) |

- Key Measures

| Measure | Data Analysis Expression (DAX) |
|-|-|
|Actual Batch Time | SUM('Line productivity'[Actual Batch Time]) |
| Down Time Pareto % | var _total = CALCULATE([Total Downtime], ALLSELECTED('Line downtime'[Description])), var _current = [Total Downtime], var _sumTable = SUMMARIZE(ALLSELECTED('Line downtime'), 'Line downtime'[Description], "DownTime", [Total Downtime]), var _cumulativeSum = SUMX(FILTER(_sumTable, [Total Downtime]>=_current), [Total Downtime]), RETURN DIVIDE(_cumulativeSum, _total) |
| Operators Down Time | CALCULATE(SUM('Line downtime'[Downtime]), 'Line downtime'[Operator error]="Yes") | |
| Overall Line Efficiency | DIVIDE(SUM('Line productivity'[Minimum Batch Time]), SUM('Line productivity'[Actual Batch Time]) , 0) |
| Overall Operators Efficiency | var Total_Minimum_Batch_Time  = SUM('Line productivity'[Minimum Batch Time]), var Total_Actual_Batch_Time = SUM('Line productivity'[Actual Batch Time]), var None_Operator_Downtime = CALCULATE(SUM('Line downtime'[Downtime]), 'Line downtime'[Operator error]="No"), var Operators_Actual_Batch_Time = Total_Actual_Batch_Time - None_Operator_Downtime, RETURN DIVIDE(Total_Minimum_Batch_Time, Operators_Actual_Batch_Time, 0) |
| Planned Batch Time | SUM('Line productivity'[Minimum Batch Time]) |
| Total Downtime | SUM('Line downtime'[Downtime]) |

## 3. Data Exploration and Visualization
- Overall Line Efficiency, Actual Batch Time, Planned Batch Time, Total Downtime (card)
- Breakdown of Downtime Causes (donut chart).
- Top 5 Downtime Factors due to Operator Errors (heat map).
- Top 5 factors that account for 80% of Total Downtime (combo line and column chart).
- Efficiency by Operator (bar chart).

## 4. Insights and Recommendations
### 4.1 Insights
- Operators caused more downtime amongst other factors.
- Batch change is major concern for Mac, and Machine adjustment  for other operators.
- Top 5 factors account for 80% of Total Downtime. 3 of these (Machine adjustment, Batch change, and Batch coding error) are due to operator errors.
- Operator Mac underperformed - below Overall Operators Efficiency.

### 4.2 Proposed Solutions
- Provide batch change training for Mac, machine adjustment training for other operators, and batch coding training for everyone.
- Leverage preventive maintenance schedules to minimize or predict machine failure.
- Upgrade or replace aging equipment with high downtime (need more data to ascertain age of equipment).
- Implement real-time tracking systems or forecasting methods to maintain optimal stock levels.
