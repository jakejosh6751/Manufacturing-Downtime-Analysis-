![image](https://github.com/user-attachments/assets/e7a70c54-9be6-4ecd-b5a5-34a37a522831)# Manufacturing Downtime Analysis:
## Optimizing Process Efficiency in Soda Bottling

### 1. Project Overview
#### 1.1 Objective
- Identify the root causes of downtime.
- Propose actionable solutions to reduce downtime.
- Optimize operational efficiency in manufacturing.

#### 1.2 Deliverables
- Downtime summary report.
- Visualizations highlighting downtime patterns and root causes.
- Recommendations for process improvements.

#### 1.3 Tool
- Visualization: Power BI

### 2. Data Description
#### 2.1 Data Source
- Maven Analytics free data sets: [data set](https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=Manu)
- Parameters: timestamps, machine IDs, downtime durations, and reasons for downtime.

#### 2.2 Data Fields

Table | Field | Description
-----|-----|-----
Line productivity | Date
 | | Product
 | | Batch
 | | Operator
 | | Start Time
 | | End Time
 | |
Products | Product
 | | Flavor
 | | Size
 | | Min batch time
 | |
Line downtime | Batch
 | | Downtime factor
 | |
Downtime factors | Factor
 | | Description
 | | Operator Error





#### 2.3 Data Cleaning
- Steps for handling missing, inconsistent, or duplicate data.

#### 2.4 Data Transformation
- Calculated Columns
- Data Analysis Expressions (DAX)

Measure | Description
----------|----------
Line Efficiency | Calculates overall efficiency

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
