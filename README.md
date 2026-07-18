# medical-supply-chain-inventory-risk-analysis
An interactive Power BI dashboard built to analyze inventory risk and revenue performance for a medical and optical retail supplier. Using 1,415 real transactions across 7 products, the project identifies which products are at risk of stockout, where revenue is concentrated, and how supplier lead time directly drives business risk — turning raw transaction data into a tool decision-makers can actually act on.

Tool: Microsoft Power BI Desktop | Dataset source: Kaggle

 Objectives
 
Identify revenue drivers — which products, categories, and regions generate the most revenue.
Quantify inventory risk — which SKUs are below their reorder point, and how severe the shortfall is.
Connect risk to operations — test whether supplier lead time actually drives risk.
Support real decisions — turn every chart into a specific, actionable recommendation.
🗂️ Dataset

Two connected CSV files, joined on SKU (one-to-many relationship):

FileRowsDescriptionInventory_Transactions.csv1,  :415One row per sale — order ID, date, SKU, quantity, location, staff, revenue, lead time, risk levelProduct_Master_List.csv7   : One row per product — description, category, supplier, unit cost, stock level, reorder point

🛠️ Methodology
Validate — checked row counts, date ranges, and null values before committing to the dataset.
Clean — fixed a date locale mismatch (5/29/2025 misread as Day/Month/Year) and corrected column data types in Power Query.
Model — built a one-to-many relationship between the two tables on SKU.
Measure — wrote DAX measures in a dedicated _Measures table, including:

Visualize — designed a 3-page dashboard: landing page, overview, and insights/recommendations.


A real data limitation — and how it was handled
During validation, Total Cost and Total Revenue measures were producing identical values. Rather than assume the formula was wrong, a temporary validation column using RELATED() traced the calculation row by row and confirmed the dataset's Revenue field was generated directly as Qty_Sold × Unit_Cost, with zero markup built in. Rather than present a misleading profitability story, the Total Cost, Total Profit, and Profit Margin % measures were removed, and the analysis was refocused on what the data genuinely supported: revenue performance, inventory risk, and supply chain operations.

🔑 Key Insights
Surgical products generate 62.75% of revenue but are also flagged for reorder — the top revenue driver carries meaningful risk.
Contact Lenses sell the highest unit volume (5.3K units), yet Surgical earns more revenue — confirming Surgical's lead comes from price per unit, not volume.
4 of 7 SKUs (57%) are currently below their reorder threshold; one SKU is overstocked by 400 units.
13.6% of orders are High Risk, concentrated in the Surgical category.
High Risk orders average a 45-day lead time — 4x longer than Low Risk orders (11 days), directly linking supplier delay to business risk.
Revenue peaked in April ($93.7K) and dipped lowest in August ($60.8K) — mild seasonality.
Regional revenue is fairly balanced: South leads ($266K), North lowest ($222K).

✅ Recommendations
Secure Surgical supply first — it's both the top revenue driver and highest-risk category.
Reorder the 4 below-threshold SKUs, prioritized by shortfall size.
Reduce procurement for the overstocked SKU to free up tied-up working capital.
Review suppliers with longer lead times — they correlate directly with higher risk.
Build buffer stock ahead of April to meet seasonal demand.
Monitor High Risk orders (1 in 7) proactively, not reactively.



👤 Author
Shibla Nasreen
Data Analyst | Power BI · Tableau · SQL · Python
