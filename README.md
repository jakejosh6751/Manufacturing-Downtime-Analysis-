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

#### Data Modeling:
Created relationships between tables in a snowflake schema, with two tables ("Products", "Line downtime") connected to a central table ("Line productivity") and a fourth table ("Downtime factors") linked to one of the two ("Line downtime"), enabling accurate data integration and analysis.

#### Calculated Columns:
Used the RELATED, IF, INT, and DATEDIFF functions to create new columns to enhance data aggregation;
* For the "Line downtime" table:
  - "Description"; and
  - "Operator error"
* For the "Line productivity" table:
  - "Actual Batch Time": and
  - "Minimum Batch Time"

#### Key Measures:
Used the CALCULATE, ALLSELECTED, SUMMARIZE, DIVIDE, SUM, SUMX, and FILTER functions to create Measures to enhance creation of Key Metrics and charts. Key Measures Include;
- Overall Line Efficiency;
- Overall Operators Efficiency;
- Actual Batch Time;
- Planned Batch Time; and
- Total Downtime.

#### Data Exploration and Visualization:
Insights were derived using the following visualizations in Power BI:

- **Cards**: Key Performance Indicators:- Overall Line Efficiency, Actual Batch Time, Planned Batch Time, Total Downtime.
- **Doughnut chart**: Breakdown of Downtime Causes.
- **Heat map**: Top 5 Downtime Factors due to Operator Errors.
- **Combo chart** (column & line): Top 5 factors that account for 80% of Total Downtime.
- **Bar chart**: Efficiency by Operator.
