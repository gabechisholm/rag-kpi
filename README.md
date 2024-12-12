# Repository Overview

This repository contains Power BI resources and scripts designed for analysing and visualising Key Performance Indicators (KPIs). It includes:

- **DAX Measures**: Predefined calculations for KPI analysis (e.g., quarter-to-quarter and year-to-year comparisons with RAG coding).
- **Power Query Script**: Automates data transformation, including extracting fiscal years and quarters.
- **Static Table**: Facilitates user-driven comparison types in reports.

These tools enable efficient trend analysis and interactive reporting for stakeholders, simplifying KPI analysis and enhancing Power BI dashboards.

---

# Table of Contents
- [MEASURE_CombinedRAG](#measure_combinedrag)
- [MEASURE_LatestDate](#measure_latestdate)
- [MEASURE_LatestValue](#measure_latestvalue)
- [MEASURE_SameQuarterDifferentYearRAG](#measure_samequarterdifferentyearrag)
- [MEASURE_PreviousQuarterRAG](#measure_previousquarterrag)
- [Power Query Script for `kpi_data`](#power-query-script-for-kpi_data)
- [ComparisonType Table](#comparisontype-table)

---

# MEASURE_CombinedRAG

## Overview
`FIN_SlicerCompare` is a DAX measure in Power BI that evaluates the performance of a selected KPI for a specific client group and indicator. It dynamically compares the latest value to a selected period and assigns a color code to indicate performance trends.

## Features
### Comparison Types (via slicer):
- **Previous Quarter Same Year**
- **Previous Year Same Quarter**

### Color Coding:
- **Green** (`#77dd77`): Improved  
- **Orange** (`#ffb347`): Same  
- **Red** (`#ff6961`): Worse  
- **Neon Blue** (`#00ffff`): Data unavailable  
- **White** (`#ffffff`): Default/no selection  

### Handles Missing Data:
Provides fallback colors for missing comparison data.

## How It Works
1. Identifies the **latest fiscal year and quarter** for the selected indicator and client group.
2. Retrieves the **latest value** and the value for the comparison period.
3. Assigns a color code based on performance trends using the selected comparison type.

## Usage
Use this measure for conditional formatting in Power BI visuals to display performance trends with intuitive color codes.

## Requirements
- **Slicer**: Options for comparison (e.g., "Previous Quarter Same Year", "Previous Year Same Quarter").
- **Data Columns**:
  - `Indicator`
  - `Client group`
  - `FisYear`
  - `Quarter`
  - `Value`

---

# MEASURE_LatestDate

## Overview
`FIN_LatestDate` is a simple DAX measure in Power BI that identifies the most recent date (`Date`) in the `kpi_data` table.

## Key Functionality
### Purpose:
- Fetches the latest date from the `Date` column of the `kpi_data` table.
### Use Case:
- Helps filter or display data associated with the most recent date, ensuring up-to-date insights.

## Usage
1. Use this measure in visuals to display the latest date or as a filter for showing only the most recent data.
2. Combine it with other measures for dynamic calculations based on the most recent data.

## Requirements
- **Data Column**:
  - `Date`

---

# MEASURE_LatestValue

## Overview
`FIN_LatestValue` is a DAX measure in Power BI that retrieves the most recent value of a selected Key Performance Indicator (KPI) for a specified client group.

## Key Features
- Dynamically identifies the **latest fiscal year and latest quarter** for the selected `Indicator` and `Client group`.
- Returns the **maximum value** of the KPI for the latest year and quarter.

## How It Works
1. **Identify Selected Context**:
   - `Indicator`: Selected via slicer or context.
   - `Client group`: Selected via slicer or context.
2. **Find Latest Period**:
   - Determines the **latest fiscal year** (`FisYear`) for the selected context.
   - Identifies the **most recent quarter** within the latest fiscal year.
3. **Retrieve Latest Value**:
   - Extracts the **maximum value** (`Value`) for the determined latest year and quarter.

## Usage
- **Visualisation**: Display the most recent KPI value for specific indicators and client groups.
- **Calculation**: Use as a base for further comparisons or trend analysis.

## Requirements
- **Data Columns**:
  - `Indicator`
  - `Client group`
  - `FisYear`
  - `Quarter`
  - `Value`

---

# MEASURE_SameQuarterDifferentYearRAG

## Overview
`FIN_PreviousYearRAG` is a DAX measure in Power BI that compares the most recent value of a Key Performance Indicator (KPI) for a selected client group to its value in the same quarter of the previous year. The measure assigns a RAG (Red-Amber-Green) colour code to indicate performance trends.

## Key Features
1. **Comparison**:
   - Compares the latest KPI value to the same quarter in the previous year.
2. **Color Coding**:
   - **Green** (`#77dd77`): Improved  
   - **Orange** (`#ffb347`): Same  
   - **Red** (`#ff6961`): Worse  
   - **Neon Blue** (`#00ffff`): Previous year's data unavailable.

## How It Works
1. **Identify Context**:
   - Selected `Indicator` and `Client group` via slicers or context.
2. **Find Periods**:
   - Determines the **latest year and quarter** for the selected context.
   - Identifies the **same quarter in the previous year**.
3. **Retrieve Values**:
   - Fetches KPI values for the **latest period** and the **previous year’s same quarter**.
4. **Apply RAG Logic**:
   - Compares values and assigns a colour code based on improvement, decline, or no change.

## Usage
- **Conditional Formatting**: Use in visuals to highlight performance trends with RAG colours.
- **Trend Analysis**: Quickly identify year-on-year performance changes for selected KPIs.

## Requirements
- **Data Columns**:
  - `Indicator`
  - `Client group`
  - `FisYear`
  - `Quarter`
  - `Value`

---

# MEASURE_PreviousQuarterRAG

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
   - Fetches KPI values for the **latest quarter** and the **previous quarter**.
4. **Apply RAG Logic**:
   - Compares values and assigns a colour code based on improvement, decline, or no change.

## Usage
- **Conditional Formatting**: Use in visuals to highlight performance trends with RAG colours.
- **Trend Monitoring**: Quickly assess quarter-on-quarter performance changes for selected KPIs.

## Requirements
- **Data Columns**:
  - `Indicator`
  - `Client group`
  - `FisYear`
  - `Quarter`
  - `Value`



# Power Query Script for `kpi_data`

## Overview
This Power Query script processes a KPI dataset from an Excel file, transforming and preparing the data for analysis. The script extracts fiscal year and quarter information from a `Date` column and ensures proper data typing for downstream usage in Power BI.

## Key Steps
1. **Source Data**:
   - Reads the data from an Excel file. Replace `"INSERT FILE PATH HERE"` with the actual file path.
   - Promotes the first row to headers.

2. **Data Type Transformation**:
   - Converts columns to their appropriate types:
     - `Indicator`: Text
     - `Client group`: Text
     - `Value`: Integer
     - `Date`: Text

3. **Extract Fiscal Year (`FisYear`)**:
   - Adds a `FisYear` column by extracting the first 4 characters from the `Date` column (assumed to represent the year).

4. **Extract Quarter (`Quarter`)**:
   - Adds a `Quarter` column by extracting the last character from the `Date` column (assumed to represent the quarter).

5. **Rename and Finalise**:
   - Renames the `Custom` column to `FisYear`.
   - Ensures correct data types for `FisYear` and `Quarter`.

## Requirements
- **Input Data**:
  - An Excel file with a sheet named `Sheet1`.
  - Columns:
    - `Indicator`: KPI name
    - `Client group`: Group being measured
    - `Value`: Numeric value of the KPI
    - `Date`: A string in `YYYYQ` format (e.g., `2023Q1`).

- **Output Data**:
  - Adds two new columns:
    - `FisYear`: Extracted fiscal year as an integer.
    - `Quarter`: Extracted quarter as an integer.

## Usage
1. Replace `"INSERT FILE PATH HERE"` with the full file path to your Excel dataset.
2. Load the script into Power Query in Power BI or Excel.
3. Ensure the input data matches the required format (e.g., `Date` column with `YYYYQ` values).
4. Use the transformed dataset for further analysis, including visualisation or KPI calculations.

---

### Notes
- Ensure the `Date` column is in `YYYYQ` format before using this script.
- Modify column names or data types in the script if your dataset's structure is different.



# ComparisonType Table

## Overview
The `ComparisonType` table is a static DAX-created table in Power BI. It defines the options available for selecting a comparison type when analysing Key Performance Indicators (KPIs).

## Structure
- **Column**: `ComparisonType` (string)
- **Values**:
  1. `Previous Quarter Same Year`: Compares the latest quarter's KPI value to the previous quarter within the same year.
  2. `Previous Year Same Quarter`: Compares the latest quarter's KPI value to the same quarter in the previous year.

## Usage
- Use this table as a slicer in your Power BI reports to allow users to select the desired comparison type.
- The selection drives dynamic measures (e.g., `FIN_SlicerCompare`) to calculate and display performance trends based on the chosen comparison type.

## Code
The table is created using the following DAX code:

```DAX
ComparisonType = DATATABLE(
    "ComparisonType", STRING,
    {
        {"Previous Quarter Same Year"},
        {"Previous Year Same Quarter"}
    }
)

