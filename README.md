# Hydropower energy modeling tool

Hydropower System Performance and Financial Analysis Modeling script 
============================================================

This script performs a comprehensive analysis of a hydropower system, calculating
its technical and financial metrics over a project's lifetime. The script handles
data preprocessing, turbine efficiency modeling, renewable energy estimation, and
cost-benefit analysis, presenting results through plots and outputs.

Key Features:
-------------
1. Load and preprocess historical flow data.
2. Calculate flow-duration and power-duration curves.
3. Model turbine efficiency and plant performance.
4. Estimate renewable energy available and firm power.
5. Perform financial analysis, including cash flow, NPV, IRR, and payback period.

Inputs:

I have used a randomy generated data for demonstration. The user have to prepare the folliwing inputs:
-------
1. Historical flow data in an Excel file with columns:
    - "Date": Timestamps of flow readings.
    - "Flow (m³/s)": Recorded flow rates.
2. Plant and turbine parameters (e.g., gross head, design flow).
3. Financial parameters (e.g., inflation rate, discount rate).

Outputs:
--------
1. Efficiency, flow, and power data tables.
2. Power-duration and cash-flow plots.
3. Key metrics: NPV, IRR, payback period, and firm power energy.



