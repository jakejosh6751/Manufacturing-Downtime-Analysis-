# Manufacturing Downtime Analysis

![manufacturing downtime report_1.jpg](https://github.com/jakejosh6751/Manufacturing-Downtime-Analysis-/blob/main/manufacturing%20downtime%20report_1.jpg)

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
Used the RELATED, IF, INT, and DATEDIFF functions to create new columns for enhanced data aggregation;
* For the "Line downtime" table:
  - "Description"
  - "Operator error"
* For the "Line productivity" table:
  - "Actual Batch Time"
  - "Minimum Batch Time"

#### Key Measures:
Utilized the CALCULATE, ALLSELECTED, SUMMARIZE, DIVIDE, SUM, SUMX, and FILTER functions to create measures for key metrics and visualizations:
- "Overall Line Efficiency"
- "Overall Operators Efficiency"
- "Actual Batch Time"
- "Planned Batch Time"
- "Total Downtime"


#### Data Exploration and Visualization:
Derived insights using the following visualizations in Power BI:

- **Cards**: Displayed Key Measures.
- **Doughnut Chart**: Showed the breakdown of downtime causes.
- **Heat Map**: Highlighted the top 5 downtime factors due to operator errors.
- **Column & Line Combo Chart** : Visualized the top 5 factors contributing to 80% of total downtime.
- **Bar Chart**: Illustrated efficiency by operator.
