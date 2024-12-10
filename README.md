# MEASURE_CombinedRAG
## Overview
FIN_SlicerCompare is a DAX measure in Power BI that evaluates the performance of a selected KPI for a specific client group and indicator. It dynamically compares the latest value to a selected period and assigns a color code to indicate performance trends.

## Features
#### Comparison Types (via slicer):
- Previous Quarter Same Year <br/>
- Previous Year Same Quarter

#### Color Coding:
- Green (#77dd77): Improved <br/>
- Orange (#ffb347): Same <br/>
- Red (#ff6961): Worse <br/>
- Neon Blue (#00ffff): Data unavailable <br/>
- White (#ffffff): Default/no selection <br/>

#### Handles Missing Data: 
Provides fallback colors for missing comparison data.

## How It Works
Identifies the latest fiscal year and quarter for the selected indicator and client group.
Retrieves the latest value and the value for the comparison period.
Assigns a color code based on performance trends using the selected comparison type.
Usage
Use this measure for conditional formatting in Power BI visuals to display performance trends with intuitive color codes.

## Requirements
Slicer: Options for comparison (e.g., "Previous Quarter Same Year", "Previous Year Same Quarter").
Data Columns: Indicator, Client group, FisYear, Quarter, Value.



# MEASURE_LatestDate
## Overview
FIN_LatestDate is a simple DAX measure in Power BI that identifies the most recent date (Date) in the kpi_data table.

## Key Functionality
### Purpose: 
- Fetches the latest date from the Date column of the kpi_data table.
### Use Case: 
- Helps filter or display data associated with the most recent date, ensuring up-to-date insights.
  
## Usage
Use this measure in visuals to display the latest date or as a filter for showing only the most recent data.
Combine it with other measures for dynamic calculations based on the most recent data.
## Requirements
Data Column: Date column in the kpi_data table.



# MEASURE_LatestValue
## Overview
FIN_LatestValue is a DAX measure in Power BI that retrieves the most recent value of a selected Key Performance Indicator (KPI) for a specified client group.

## Key Features
Dynamically identifies the latest fiscal year and latest quarter for the selected Indicator and Client group.
Returns the maximum value of the KPI for the latest year and quarter.
## How It Works
1. Identify Selected Context:
   - Indicator: Selected via slicer or context.
   - Client group: Selected via slicer or context.
2. Find Latest Period:
   - Determines the latest fiscal year (FisYear) for the selected context.
   - Identifies the most recent quarter within the latest fiscal year.
3. Retrieve Latest Value:
   - Extracts the maximum value (Value) for the determined latest year and quarter.
## Usage
- Visualisation: Display the most recent KPI value for specific indicators and client groups.
- Calculation: Use as a base for further comparisons or trend analysis.
## Requirements
Data Columns:
- Indicator
- Client group
- FisYear
- Quarter
- Value



# MEASURE_SameQuarterDifferentYearRAG
## Overview
FIN_PreviousYearRAG is a DAX measure in Power BI that compares the most recent value of a Key Performance Indicator (KPI) for a selected client group to its value in the same quarter of the previous year. The measure assigns a RAG (Red-Amber-Green) colour code to indicate performance trends.

## Key Features
1. Comparison:
   - Compares the latest KPI value to the same quarter in the previous year.
2. Color Coding:
   - Green (#77dd77): Improved
   - Orange (#ffb347): Same
   - Red (#ff6961): Worse
   -Neon Blue (#00ffff): Previous year's data unavailable.
## How It Works
1. Identify Context:
   -Selected Indicator and Client group via slicers or context.
2. Find Periods:
   - Determines the latest year and quarter for the selected context.
   - Identifies the same quarter in the previous year.
3. Retrieve Values:
   - Fetches KPI values for the latest period and the previous year’s same quarter.
4. Apply RAG Logic:
   - Compares values and assigns a colour code based on improvement, decline, or no change.
## Usage
- Conditional Formatting: Use in visuals to highlight performance trends with RAG colours.
- Trend Analysis: Quickly identify year-on-year performance changes for selected KPIs.
### Requirements
- Data Columns:
- Indicator
- Client group
- FisYear
- Quarter
- Value




# FIN_PreviousQuarterRAG Measure: README

## Overview
`FIN_PreviousQuarterRAG` is a DAX measure in Power BI that compares the latest value of a Key Performance Indicator (KPI) to its value in the previous quarter. It assigns a RAG (Red-Amber-Green) colour code to indicate performance trends over the most recent quarter.

## Key Features
1. **Comparison**:
   - Evaluates the KPI value in the latest quarter against the previous quarter.
   - Adjusts for fiscal year changes if the latest quarter is Q1.

2. **Color Coding**:
   - **Green** (`#77dd77`): Improved  
   - **Orange** (`#ffb347`): Same  
   - **Red** (`#ff6961`): Worse  
   - **White** (`#ffffff`): Default if comparison cannot be determined.

## How It Works
1. **Identify Context**:
   - Selected `Indicator` and `Client group` via slicers or context.
2. **Find Periods**:
   - Determines the **latest year and quarter** for the selected context.
   - Identifies the **previous quarter** and adjusts the year if necessary (e.g., Q1 to Q4 of the previous year).
3. **Retrieve Values**:
   - Fetches KPI values for the latest quarter and the previous quarter.
4. **Apply RAG Logic**:
   - Compares values and assigns a colour code based on improvement, decline, or no change.

## Usage
- **Conditional Formatting**: Use in visuals to highlight performance trends with RAG colours.
- **Trend Monitoring**: Quickly assess quarter-on-quarter performance changes for selected KPIs.

---

### Requirements
- **Data Columns**:
  - `Indicator`
  - `Client group`
  - `FisYear`
  - `Quarter`
  - `Value`

This measure provides stakeholders with clear insights into short-term KPI performance trends for effective decision-making.
