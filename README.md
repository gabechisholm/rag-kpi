# MEASURE_CombinedRAG
## Overview
FIN_SlicerCompare is a DAX measure in Power BI that evaluates the performance of a selected KPI for a specific client group and indicator. It dynamically compares the latest value to a selected period and assigns a color code to indicate performance trends.

## Features
Comparison Types (via slicer):

Previous Quarter Same Year
Previous Year Same Quarter
Color Coding:

Green (#77dd77): Improved
Orange (#ffb347): Same
Red (#ff6961): Worse
Neon Blue (#00ffff): Data unavailable
White (#ffffff): Default/no selection
Handles Missing Data: Provides fallback colors for missing comparison data.

## How It Works
Identifies the latest fiscal year and quarter for the selected indicator and client group.
Retrieves the latest value and the value for the comparison period.
Assigns a color code based on performance trends using the selected comparison type.
Usage
Use this measure for conditional formatting in Power BI visuals to display performance trends with intuitive color codes.

## Requirements
Slicer: Options for comparison (e.g., "Previous Quarter Same Year", "Previous Year Same Quarter").
Data Columns: Indicator, Client group, FisYear, Quarter, Value.
