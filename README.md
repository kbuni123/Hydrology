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

Equations:
-----------
Flow Duration Curve
================

- A flow duration is produced from historical flow data.
- The flow-duration curve is specified by twenty-one values representing the flow on the flow-duration curve in 5% increments.
- the produced FDC Highlights design flow and firm flow thresholds.
  ![image](https://github.com/user-attachments/assets/797bab9a-5260-441c-8936-2cc1127a09d5)



The model currently supports Pelton turbines, but I am planning to add more turbine types in future updates!

**Rotational Speed and Runner Diameter of pelton turbine:**
- Rotational Speed: $$RPM = \frac{31 . H_{rated}. Q_{design} }{ j }$$
- Runner Diameter: $$D =\frac{ 49.4 . H_{rated} .{j}^{0.02} }{ RPM}$$
- $j$= number of jets

*Pelton Turbine Efficiency Calculations:**
- Turbine Peak Efficiency: $$e_p= 0.864 . D^{0.04}$$
- Peak Efficiency Flow: $$Q_p = (0.662 + 0.001 × j) . Q_{design}$$
- Efficiency at Specific Flow : $$e_t = e_p (1 - (1.31 + 0.025 j) . |\frac{ Q_p - Q }{ Q_p}|^{5.6 + 0.4 j})
$$


Power and Energy output Calculation
============================
- Actual power P available from the small hydro plant at any given flow value Q is given by the following equation:


$$P = ρ  .g  .Q_{values}  .H_{net} . e_{t} . e_{g} .(1 - l_{t}) .(1 - l_{para})$$ 

Where:
- $H_{net}$= Net head
- $l_{t}$ = transformer losses
- $l_{para}$= parasitic losses
- $e_{g}$=generator effeciency (user input)
  

- Net head calculation:
$$H_{net} = H_{rated} - H_{loss} - H_{tailwater}$$


**Hydraulic Losses and Tailwater Effects:**

- Hydraulic Loss:

$$
H_{loss} = H_{gross} \cdot 0.03 \cdot \left(\frac{Q_{values}}{Q_{design}}\right)^2
$$

- Tailwater Effect:
$$H_{tailwater} = 0 \quad \text{if } \quad Q \leq Q_{design}$$

$$H_{tailwater}=3 * (\frac{Q - Q_{design}}{ Q_{max} - Q_{design}})^ 2 \quad \text{if } \quad Q> Q_{design}
$$


**Plant Capacity**
- Plant capacity $P_{des}$ is calculated by re-writing the power equation above at the design flow $Q_{des}$.

Power-duration curve
====
- Calculation of power available as a function of flow using the power equation for all 21 values of the available flow that are used to define the flow-duration curve, leads to 21 values of available power defining a power-duration curve.

- Since the design flow is defined as the maximum flow that can be used by the turbine, the value of $Q_{des}$ is employed for flow quantities exceeding the design flow.

![image](https://github.com/user-attachments/assets/ead9f5fb-07a2-4117-8caf-5f3893c9abac)


   Cost Analysis and Financial Indicators.
====
**Net Present Value (NPV)**

- Net Present Value (NPV) is a method used to evaluate the profitability of a project or investment by summing the present values of all cash flows (inflows and outflows) over the life of the project.

$$NPV = \sum_{t=0}^{n} \frac{C_{t} }{ (1 + r)^t}$$

Where:
- $C_{t}$= cash flow at time t
- $r$ = Discount rate (reflecting the time value of money)
- $t$ = Year (from 0 to n)
- $n$ = Project life (total number of years)






**Internal Rate of Return (IRR)**

- The Internal Rate of Return (IRR) is the discount rate (𝑟) at which the Net Present Value (NPV) of an investment becomes zero. In simpler terms, it is the annualized rate of return that a project or investment is expected to generate.

$$NPV = \sum_{t=0}^{n} \frac{C_{t} }{ (1 + IRR)^t}=0$$ 




**Payback period**

- The Payback Period is the time it takes for a project to recover its initial investment through its cumulative cash inflows. In other words, it’s the point where the cumulative cash flow turns positive.


**Year to Positive Cash Flow**

-The Year to Positive Cash Flow is the first year when the cumulative cash flow becomes non-negative. It tells you the earliest point when the project stops losing money and starts generating a net positive return.









