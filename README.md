# Amazon Revenue Decision Intelligence

A business analytics case study that examines revenue concentration, cancellation/return leakage, and potential growth levers in an Amazon India order dataset. The analysis is framed around a decision question: should the business prioritize leakage reduction or average order value (AOV) improvement?

## Business Question

Which controllable lever offers the stronger revenue opportunity: recovering revenue lost to cancellations and returns, or increasing the value of completed orders?

## Analysis Workflow

1. **Data preparation** — inspect order records, normalize order status, and distinguish completed revenue from leakage.
2. **Revenue definition** — establish the revenue basis used in the analysis and aggregate by category and geography.
3. **Exploratory analysis** — examine order value distributions and revenue concentration.
4. **Outlier analysis** — use IQR-based inspection to identify high-value orders for business interpretation rather than automatically removing them.
5. **Scenario analysis** — compare an assumed 20% leakage reduction with an assumed 5% AOV increase.
6. **Decision framing** — compare scenario outputs and identify the lever with the higher modeled upside.

## Reported Findings

The notebook reports the following conclusions for the analyzed dataset and assumptions:

- Approximately 3% of orders account for approximately 7% of revenue.
- In the modeled scenarios, a 5% AOV increase produces a larger revenue impact than a 20% reduction in leakage.
- The resulting recommendation is to prioritize product-mix and premium-offering opportunities while protecting high-value orders from preventable leakage.

These are dataset-specific analytical findings, not causal estimates or guaranteed business outcomes.

## Repository Contents

```text
.
├── README.md
└── amazon-revenue-decision-intelligence.ipynb
```

The notebook contains the end-to-end analysis, calculations, and interpretation.

## Technology

- Python
- pandas
- NumPy
- Jupyter Notebook

## How to Explore

1. Clone this repository.
2. Open `amazon-revenue-decision-intelligence.ipynb` in Jupyter Notebook or JupyterLab.
3. Review the data preparation and revenue definitions before interpreting the scenario outputs.

The notebook's data inputs and analysis assumptions should be checked when reproducing or extending the work.

## Limitations

- The analysis is based on historical order data and the specific geography/time period represented in the dataset.
- Cost and margin information was not available, so revenue impact should not be confused with profit impact.
- The scenario calculations assume no material demand-elasticity response to AOV changes.
- The 20% leakage-reduction and 5% AOV-uplift values are scenario assumptions, not observed interventions.
- The reported relationship does not establish that changing AOV will cause the projected revenue gain.


---

**Sai Datta Putta**

[LinkedIn](https://www.linkedin.com/in/sai-datta-putta/)
