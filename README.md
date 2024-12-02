# Manufacturing Downtime Analysis:
## Optimizing Process Efficiency in Soda Bottling

### 1. Project Overview
Downtime in manufacturing refers to periods when production is halted, impacting efficiency, productivity, and profitability. It can stem from equipment failure, maintenance, operator, or supply chain issues, leading to significant operational costs.

Analyzing downtime is crucial for identifying root causes, minimizing disruptions, and optimizing workflows. By addressing downtime effectively, companies can achieve higher production reliability and cost savings.

#### 1.1 Objective
- Identify the root causes of downtime.
- Propose actionable solutions to reduce downtime.
- Optimize operational efficiency in manufacturing.

#### 1.2 Deliverables
- Downtime summary report.
- Visualizations highlighting downtime patterns and root causes.
- Recommendations for process improvements.

#### 1.3 Tool
- Power BI

### 2. Data Preparation
#### 2.1 Data Source
- Maven Analytics free data sets: [data set](https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=Manu)

#### 2.2 Data Tables & Fields
Table | Field | Description
-----|-----|-----
Line productivity (Fact table) | Date | Date the batch was produced
 | | Product | ID for the product produced in the batch
 | | Batch | Unique ID for the batch produced
 | | Operator | Production line operator in charge of the batch
 | | Start Time | Time the batch production started
 | | End Time | Time the batch production ended
 | |
Products (Dimension table) | Product | Unique product ID
 | | Flavor | Soda flavor for the product
 | | Size | Product size (volume)
 | | Min batch time | Minimum time required to produce a batch (with no downtime)
 | |
Line downtime (Fact table) | Batch | Unique ID for the batch produced
 | | Downtime factor | Downtime minutes for each factor ID (across columns)
 | |
Downtime factors (Dimension table) | Factor | Unique ID for each downtime factor
 | | Description | Downtime factor description
 | | Operator Error | Is this due to operator error? (Yes/No)

#### 2.3 Data Cleaning
* Downtime factors table
  - Changed column name 'Factor' to 'Downtime Factor'
* Line downtime table
  - Removed first row: has only one column title (Downtime factor) representing multiple parameters.
  - Promoted first row to headers.
  - Replaced null values in column '1' with 0. This is to ensure the downtime description 'Emergency stop' represented by 1 appears in visuals.
  - Unpivoted other columns except 'Batch'.
  - Renamed columns 'Attribute' to 'Downtime Factor', 'Value' to 'Downtime', and changed data types.

#### 2.4 Data Modeling

#### 2.5 Data Transformation
- Calculated Columns

Table | Column | Expression | Function
|-----|-----|-----|-----|
Line downtime | Description | RELATED('Downtime factors'[Description]) | Looks up Description from 'Downtime factors' table and [Description] column
| | Operator error | RELATED('Downtime factors'[Operator Error]) | 
| | | | 
Line productivity | Actual Batch Time | IF(INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)<0, INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)+1440, INT(DATEDIFF('Line productivity'[Start Time], 'Line productivity'[End Time], SECOND)/60)) | 
  
- Measures

Measure | Data Analysis Expression (DAX) | Function
-----|-----|-----
Line Efficiency | | Calculates overall efficiency

### 3. Data Exploration and Visualization
- Downtime distribution (box plots or histograms).
- Downtime trends over time (line charts).
- Downtime reasons by machine (bar charts).

### 4. Insights and Recommendations
#### 4.1 Insights

#### 4.2 Proposed Solutions
- Preventive maintenance schedules.
- Improved operator training.
- Upgraded equipment for high-downtime machines.
