# Amazon Revenue Decision Intelligence

A business analytics case study using the Amazon Sale Report dataset to examine fulfilled revenue, cancellation/return leakage, category concentration, high-value records, state-level variation, and what-if revenue scenarios.

The analysis is structured around a practical decision: compare the modeled upside of a hypothetical average-value uplift with the modeled recovery from reducing revenue leakage.

## Business Question

For the observed Amazon India sales records, which illustrative lever produces the larger gross-revenue impact: reducing leakage or increasing the average value of revenue-generating records?

## Dataset and Scope

- **Dataset:** Amazon Sale Report, obtained in the notebook through KaggleHub from thedevastator/unlock-profits-with-e-commerce-sales-data
- **Rows in source report:** 128,975
- **Core fields used:** date, status, fulfilment, service level, category, quantity, amount, city, and state
- **Period:** the 2022 sale-report data represented by the source file

The notebook classifies records by fulfilment status. It retains the original status categories and does not treat all rows as completed sales.

## Results and Business Findings

The figures below are taken from saved notebook outputs, not recalculated during this README update.

### 1. Record segmentation

| Group | Records |
|---|---:|
| Revenue-generating statuses | 107,589 |
| Leakage / non-revenue statuses | 21,105 |
| Total classified records | 128,694 |

The revenue-generating group includes Shipped, Shipped - Delivered to Buyer, Shipped - Picked Up, Shipped - Out for Delivery, and Shipping. The leakage group includes cancelled, returned, pending, rejected, lost, and damaged statuses.

The source has 128,975 rows; 281 rows fall outside the two status lists used by the notebook and are not represented in the above classified total.

### 2. Revenue and order-value profile

| Measure | Saved result |
|---|---:|
| Gross Amount across revenue-group rows | ₹69,663,293 |
| Quantity across revenue-group rows | 107,915 |
| Non-null Amount values in revenue-group rows | 107,365 |
| Mean non-null Amount | ₹648.85 |
| Median Amount | ₹603 |
| Maximum Amount | ₹5,584 |

The notebook also calculates **₹647.49** by dividing total Amount by 107,589 revenue-group rows. This is a row-level average, not a verified unique-order AOV: the code uses dataframe row count rather than counting distinct Order IDs.

### 3. Revenue mix by category

Share of revenue-group Amount by category:

| Category | Revenue share |
|---|---:|
| Set | 49.86% |
| Kurta | 27.17% |
| Western Dress | 14.11% |

The three categories together represent approximately 91.15% of the category revenue total in the notebook's calculation.

### 4. High-value records

Using the IQR rule on Amount, the notebook identifies 3,266 high-value records:

| Measure | Result |
|---|---:|
| Outlier records | 3,266 |
| Share of revenue-group rows | 3.04% |
| Amount represented by outlier records | ₹4,682,454 |
| Share of revenue-group Amount | 6.72% |

Most detected outlier records belong to the Set category (3,169 records). The notebook keeps these records in its revenue analysis rather than automatically discarding them.

### 5. Leakage and scenario comparison

The leakage group contains 21,105 records. The non-null Amount values in those rows sum to **₹8,737,247.30**. The notebook's scenario calculations are:

| Scenario | Assumption | Modeled gross-revenue impact |
|---|---|---:|
| Reduce leakage | Recover 20% of leakage Amount | +₹1,747,449.46 |
| Increase average row value | Increase calculated row-average amount by 5% | +₹3,483,164.65 |
| Lose all high-value outlier records | Remove the outlier Amount contribution | −₹4,682,454.00 |

Under these assumptions, the 5% average-value scenario is approximately twice the modeled impact of the 20% leakage-reduction scenario. This is a static what-if comparison, not the result of a live experiment or a causal estimate.

### 6. Geographic variation

The notebook's top five state-level value-per-unit calculation (Amount divided by quantity) is:

| State | Amount | Quantity | Amount per unit |
|---|---:|---:|---:|
| Bihar | ₹1,432 | 1 | ₹1,432.00 |
| Ladakh | ₹31,229 | 34 | ₹918.50 |
| Sikkim | ₹2,703 | 3 | ₹901.00 |
| Chandigarh | ₹7,752 | 9 | ₹861.33 |
| Lakshadweep | ₹2,441 | 3 | ₹813.67 |

Some of these values have very small quantities; they indicate descriptive pockets of higher per-unit order value, not statistically stable state rankings.

## Decision Implication

The notebook's scenario arithmetic favours testing product-mix or basket-value improvements before prioritizing leakage reduction alone. A reasonable next step would be a controlled experiment on bundles or premium assortment while continuing operational work on cancellations and returns.

The business recommendation should be considered provisional because the average-value scenario uses row count, not distinct orders, and the leakage group includes pending statuses as well as completed cancellation/return outcomes.

## Workflow

1. Load the source sale-report CSV.
2. Select sales, fulfilment, quantity, amount, and geography fields.
3. Parse dates and derive a month field.
4. Inspect missingness and distribution of order statuses.
5. Classify records into revenue-generating and leakage groups.
6. Analyze category and state-level revenue patterns.
7. Identify high-value Amount records using IQR.
8. Compare static leakage-reduction, average-value-uplift, and high-value-loss scenarios.

## Repository Contents

- amazon-revenue-decision-intelligence.ipynb — data preparation, calculations, saved outputs, and business interpretation
- README.md — project documentation

The input CSV is referenced through KaggleHub and is not stored in this repository.

## Technology

Python, pandas, NumPy, KaggleHub, and Jupyter Notebook.

## Reproducing the Analysis

The notebook retrieves the dataset using KaggleHub and was developed in a Kaggle notebook environment. To reproduce outside that environment:

1. Install Python and Jupyter.
2. Install pandas, NumPy, and KaggleHub.
3. Configure Kaggle access as required by KaggleHub.
4. Download the dataset and update the CSV path in the notebook.
5. Run the notebook cells in order.

## Data Quality and Interpretation Limitations

- The source has 128,975 rows, but the two status lists used in the notebook classify 128,694 rows; 281 rows are not included in either group.
- Amount is missing in 7,795 source rows. The revenue-group frame has 224 missing Amount values, and the leakage frame has 7,571 missing Amount values.
- The leakage group includes Pending records and statuses that may not represent a finalized lost sale.
- The calculation named AOV divides Amount by revenue-group row count; distinct Order IDs are not counted in that calculation.
- The scenario outputs are assumptions-based gross-revenue estimates, not profit estimates, because cost/margin data is not included.
- The 5% average-value scenario assumes no demand elasticity or volume change.
- State rankings based on very low quantities should be interpreted cautiously.
- The notebook prints a mixed-type warning for one source column.

## Recommended Improvements

Reconcile all status categories, decide how pending records should be handled, calculate AOV using distinct order IDs, quantify scenario sensitivity to missing Amount data, and test the proposed uplift through an experiment before treating it as an actionable business forecast.

---

**Sai Datta Putta**

[LinkedIn](https://www.linkedin.com/in/sai-datta-putta/)
