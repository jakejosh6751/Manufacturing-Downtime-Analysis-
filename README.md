# Manufacturing Downtime Analysis in Soda Bottling

## Project Overview
Downtime in manufacturing refers to periods of halted production due to equipment failure, maintenance, operator errors, or supply chain issues, leading to reduced efficiency and profitability. Analyzing downtime is essential for identifying root causes, minimizing disruptions, and streamlining workflows. Effective downtime management enhances production reliability and drives cost savings, ultimately boosting operational performance.

I conducted a productivity and downtime analysis for a soda bottling production line, examining batch-level data that included operator performance, product type, start and end times, and downtime factors. This analysis helped identify key inefficiencies and opportunities for optimizing production workflows.

## Key Objectives
- **Downtime Analysis**: Identify and evaluate factors contributing to production halts.
- **Productivity Assessment**: Analyze batch-level productivity metrics.
- **Operator Performance**: Assess the impact of operator efficiency on production.
- **Process Optimization**: Uncover opportunities to streamline workflows and reduce downtime.

## Key Insights & Recommendations

![manufacturing downtime report_2.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis-/blob/main/manufacturing%20downtime%20report_2.jpg)

## Techniques & Procedures

#### Data Cleaning Process:

* Extracted and loaded all four tables from separate sheets in one Excel workbook into Power BI.
* For the "Downtime factors" table, renamed the "Factor" column to "Downtime Factor".
* For the "Line downtime" table:
  - Removed the first row containing a single title that represented multiple parameters.
  - Promoted the new first row to headers.
  - Replaced null values in the "1" column with 0 to ensure the "Emergency stop" downtime description is accurately displayed in visuals.
  - Unpivoted all columns except "Batch".
  - Renamed "Attribute" to "Downtime Factor" and "Value" to "Downtime",  then adjusted data types accordingly.








#### Schema:
- Tables are related by snowflake schema.
- fact table... rows, columns
- Dimension tables...

#### Calculated Columns:
#### Key Measures:
#### Data Exploration and Visualization:
Insights were derived using the following visualizations in Power BI:

- Cards: Key Performance Indicators:- Overall Line Efficiency, Actual Batch Time, Planned Batch Time, Total Downtime.
- Doughnut chart: Breakdown of Downtime Causes.
- Heat map: Top 5 Downtime Factors due to Operator Errors.
- Combo chart (column & line): Top 5 factors that account for 80% of Total Downtime.
- Bar chart: Efficiency by Operator.






# Calculated Columns
| Table | Calculated Column | Expression |
|-|-|-|
| Line downtime | Description | RELATED('Downtime factors'[Description]) |
| | Operator error | RELATED('Downtime factors'[Operator Error]) |
| | | |
| Line productivity | Actual Batch Time | IF(INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)<0, INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)+1440, INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)) |
| | Minimum Batch Time | RELATED(Products[Min batch time]) |

# Key Measures
| Measure | Data Analysis Expression (DAX) |
|-|-|
|Actual Batch Time | SUM('Line productivity'[Actual Batch Time]) |
| Down Time Pareto % | var _total = CALCULATE([Total Downtime], ALLSELECTED('Line downtime'[Description])), var _current = [Total Downtime], var _sumTable = SUMMARIZE(ALLSELECTED('Line downtime'), 'Line downtime'[Description], "DownTime", [Total Downtime]), var _cumulativeSum = SUMX(FILTER(_sumTable, [Total Downtime]>=_current), [Total Downtime]), RETURN DIVIDE(_cumulativeSum, _total) |
| Operators Down Time | CALCULATE(SUM('Line downtime'[Downtime]), 'Line downtime'[Operator error]="Yes") | |
| Overall Line Efficiency | DIVIDE(SUM('Line productivity'[Minimum Batch Time]), SUM('Line productivity'[Actual Batch Time]) , 0) |
| Overall Operators Efficiency | var Total_Minimum_Batch_Time  = SUM('Line productivity'[Minimum Batch Time]), var Total_Actual_Batch_Time = SUM('Line productivity'[Actual Batch Time]), var None_Operator_Downtime = CALCULATE(SUM('Line downtime'[Downtime]), 'Line downtime'[Operator error]="No"), var Operators_Actual_Batch_Time = Total_Actual_Batch_Time - None_Operator_Downtime, RETURN DIVIDE(Total_Minimum_Batch_Time, Operators_Actual_Batch_Time, 0) |
| Planned Batch Time | SUM('Line productivity'[Minimum Batch Time]) |
| Total Downtime | SUM('Line downtime'[Downtime]) |
