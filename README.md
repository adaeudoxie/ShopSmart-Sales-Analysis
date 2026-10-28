# ShopSmart-Sales-Analysis
This project is an end-to-end retail analysis performed using Microsoft Excel. It involved cleaning 9 datasets relating to 50,000 orders, applying Excel functions, creating Pivot Tables, generating an interactive dashboard, and providing business recommendations based on the results obtained from analysis.

> Completed as part of the **AnalystLab Africa Experience Lab**, Data Analytics Track, Week 1.

---

## Business Problem
ShopSmart's management wanted to understand its 2025 sales performance and answer questions such as:
- Which products, stores, categories and months generate the most revenue?
- Who are the highest-spending customers?
- Which products are returned most often, and which stores are running low on stock?
- Which region performs best, and which category should management invest in?

## Dataset
Nine CSV files covering **1 January – 31 December 2025** were provided for this analysis. They can be viewed here.

### Data Model
The data follows a star schema, with Orders as the central fact table.


## Tools & Skills Used
**Microsoft Excel**
- Data cleaning: Power Query
- Excel Tables and structured references
- Excel Formulas
- Lookups
- PivotTables
- Interactive dashboard with slicers
- Business analysis and reporting

## Project Workflow
1. Data understanding: the files were inspected to identify each dataset's purpose, primary and foreign keys, and the relationships with other tables.
2. Data cleaning:
   - Imported files into Power Query
   - Checked for duplicates (0 duplicate rows, 0 duplicate keys) and missing values (0 blanks)
   - Converted 6 text date columns into real Excel dates, and ensured all dates had the same format (DD/MM/YY)
   - Confirmed all currency fields are numeric and applied ₦ formatting
   - Converted every dataset into a named Excel Table
3. Monetary transactions were analyzed to determine important business figures such as Total Price, Refunds, Net Revenue, and more.
4. Analysis: PivotTables and PivotCharts were created to represent findings based on categories.
6. Dashboard design
7. Insights and recommendations: the business questions were answered in a report.

## Revenue Methodology
Revenue per sale is calculated for each order as follows:

| Step | Calculation |
|---|---|
| 1 | Total Price = Quantity × Unit Price |
| 2 | Discount Amount = Total Price × Discount % |
| 3 | Discounted Price = Total Price − Discount Amount |
| 4 | Amount Payable = Discounted Price + Shipping Cost |
| 5 | Revenue per Sale = Amount Payable − Refund Amount |
| 6 | **Total Revenue = sum of Revenue per Sale for Completed orders only** |

Only completed orders were used in processing the revenue and other finaicl figures, as they were the only orders that can be confirmed to have pulled money into the business.

## Dashboard
![Executive Dashboard]((https://github.com/adaeudoxie/ShopSmart-Sales-Analysis/blob/main/Dashboard/Executive%20Dashboard.png))

| KPI | Value |
|---|---|
| Total Revenue (completed orders) | **₦2.27bn** |
| Orders placed | 50,000 |
| Completed orders | 16,529 (33.1%) |
| Customers | 5,000 |
| Average Order Value | ≈ ₦137.41K |
| Return Rate | 5% |
| Inventory Value (at cost) | ₦3.17bn |

## Key Findings
1. *Order conversion is the biggest constraint on growth.* A total of 50,000 orders were placed, but only 16,529 (33.06%) of them were completed, 16,861 (33.72%) were canceled, and 16,610 (33.22%) were still pending at the time of analysis.
2. *Returns are majorly caused by operational factors.* 5% of orders are returned (₦61.84M refunded). Cumulatively, Late Delivery and Wrong Item cause 51% of returns, and these factors can be fixed in the business operations. Additionally, 1,685 returns were recorded against orders that were cancelled or never completed.
3. *Refund controls are weak.* The analysis revealed 270 refunds larger than the sales amount.

### Business Questions
| Question | Answer |
|---|---|
| Highest-revenue product | Beauty Item 210 |
| Best store | ShopSmart Lagos (STR003) |
| Top category | Beauty |
| Highest-revenue month | December |
| Top customer | Melissa Shaffer (CUST03257) |
| Most returned products | Beauty Item 114 and Home Item 263 (11 returns each) |
| Stores with low inventory | Lagos (STR013) and Ibadan (STR003) |
| Best region | South |
| Category to invest in | Beauty |

### Recommendations
1. *Lost Order Recovery.* ShopSmart should implement a weekly order-status review where they follow up every pending order within 48 hours and add a mandatory cancellation-reason code at checkout and in-store.
2. *Investment Areas.* The business can expand the Beauty category and promotions in the South region. They should also keep Groceries as a stable pillar, as that category has the lowest return rate (4.71%).
3. *Tighten returns and refunds.* Improve pick-and-pack checks to tackle sending out wrong items, and delivery SLAs to tackle late deliveries. Implementing a digital system that blocks refunds above the sale value or on cancelled orders would tackle net-negative returns.

### Risk & Opportunity
**Risk:** inconsistent master data (regions, prices) could lead to wrong decisions until it is fixed at source.
**Opportunity:** loyalty tiers don't reflect real spending; re-tiering customers on actual spend could grow repeat revenue.

## Data Quality Issues
1. **Line_Total disparity:** the source Line_Total subtracts the discount as a naira amount, but the values (0, 5, 10, 15, 20) are percentage tiers. Recalculating with percentages shows the source Line_Total overstates completed sales by **₦250.0M (11.1%)** across 13,207 orders.
2. **Inconsistent regions:** the same state is assigned to different regions (Lagos stores are labelled South, East, North and West).
3. **Invalid returns:** 1,252 returns are dated before their order, 1,685 relate to cancelled or pending orders, and 270 refunds exceed the sale value.
4. **Pricing:** order prices never match catalogue prices, and 12,163 orders are priced below cost.

## Limitations & Assumptions
1. The provided datasets span only one year, so year-on-year growth can't be measured.
2. Inventory is a single snapshot, so stock turnover cannot be measured.
3. Employees aren't linked to orders, so staff performance cannot be analyzed.
4. Discount is assumed to be a percentage, and revenue counts completed orders only.
