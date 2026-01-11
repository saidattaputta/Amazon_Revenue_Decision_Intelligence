# Amazon Revenue Decision Intelligence

## Overview
This project analyzes Amazon India sales data to identify **revenue concentration risks**, **revenue leakage drivers**, and **high-impact growth levers**.  
The focus is not just on analysis, but on **decision-making** — answering *what should be done next* and *why*.

The project is structured as a **decision intelligence case study**, similar to how analytics teams support leadership decisions in real organizations.

---

## Business Problem
Management is concerned about:
- Revenue volatility
- High cancellations and returns
- Over-dependence on a small set of products or regions

The key question:
> **Which levers should be prioritized to sustainably grow revenue — volume, value (AOV), or leakage reduction?**

---

## Key Questions Addressed
- Where is revenue coming from, and how concentrated is it?
- How much revenue is lost due to cancellations and returns?
- Are high-value orders driving disproportionate revenue?
- Which strategy has higher impact:
  - Reducing revenue leakage  
  - Increasing Average Order Value (AOV)

---

## Approach
1. **Data Cleaning & Preparation**
   - Order segmentation by revenue vs leakage
   - Handling missing values and inconsistent statuses

2. **Revenue Definition & Decomposition**
   - Clear separation of revenue-generating vs leakage orders
   - Category- and state-level revenue breakdown

3. **Exploratory Data Analysis (EDA)**
   - Distribution analysis of order value
   - Revenue concentration analysis
   - Category and regional performance

4. **Outlier Analysis**
   - IQR-based identification of high-value orders
   - Business interpretation of outliers (not blind removal)

5. **Scenario Simulation (What-If Analysis)**
   - Revenue impact of:
     - 20% leakage reduction
     - 5% increase in Average Order Value
   - Comparison of upside and controllability

---

## Key Insights
- ~3% of orders contribute ~7% of total revenue, indicating **high revenue concentration**
- Revenue leakage exists, but its recovery potential is limited compared to value-based growth
- A small increase in AOV generates **higher revenue impact** than aggressive leakage reduction
- Product category mix is the most controllable and scalable growth lever

---

## Final Decision
**Prioritize Average Order Value (AOV) growth through product mix optimization and premium offerings**, while selectively protecting high-value orders from leakage.

This strategy delivers higher revenue impact with better controllability and lower operational risk.

---

## Tools & Technologies
- Python
- Pandas
- NumPy
- Jupyter Notebook
- Kaggle Dataset

---

## Project Type
- Decision Intelligence
- Business Analytics
- Revenue Strategy Analysis

---

## Notes & Limitations
- Analysis is based on historical order data
- Cost and margin data were not available
- Scenario results assume no major demand elasticity effects
- Findings are specific to the analyzed time period and geography (India)

---

## Author
Sai Datta Putta
