# Procurement & Supplier Performance Analytics Dashboard
### A Power BI case study

**One-line summary:** A 3-page Power BI dashboard built to evaluate supplier performance across spend, delivery, quality, and lead time — designed the way a procurement or SCM team would actually use it, from executive overview down to operational drill-down.

---

## Why I built this

Most student Power BI projects stop at "connect a dataset, drop in some visuals." I wanted to build something closer to what a procurement or supply chain analyst is actually asked to produce: a supplier scorecard that a category manager could open on a Monday morning and immediately know which suppliers need attention, and why.

The scenario: a mid-sized manufacturing/auto-components procurement function tracking supplier performance across cost, delivery reliability, and quality — the same kind of KPI set you'd expect at a company like TVS Motor or Ashok Leyland. *(Data is fully synthetic — no real supplier or company data was used.)*

## Data model & approach

Rather than building everything off one flat table, I modeled it as a proper star schema:

- **Dim_Supplier** — supplier name, country, supplier category
- **Product_Master** — product/category hierarchy
- **Dim_Quality** — defect type reference
- **Fact_PurchaseOrders** — the transactional grain: PO date, spend, quantities
- **Supplier Measure** — a dedicated, disconnected measures table holding all DAX calculations (Total Spend, On-Time Delivery %, Defect Rate %, Supplier Score, Avg Lead Time Days, Total Orders)

Keeping measures in their own disconnected table rather than scattering them across fact/dimension tables keeps the field list clean and makes the model easier to explain and maintain — a habit carried over from formal data modeling practice rather than default drag-and-drop building.

All three report pages share a synced filter set (Supplier Name, Country, Category), so a filter applied on one page holds when you navigate to the next — the dashboard behaves like one connected tool rather than three separate reports.

## Page 1 — Executive Summary

The landing page, built for a 10-second read: five KPI cards across the top (Total Spend, On-Time Delivery %, Defect Rate %, Supplier Score, Avg Lead Time Days), followed by Total Spend by Supplier, Total Spend by Category, Total Spend by Month, and a full Supplier Performance Scorecard table for anyone who wants the underlying numbers.

This page answers one question: *at a glance, how healthy is our supplier base right now?*

## Page 2 — Supplier Performance Analysis

Where the leadership summary ends, the analyst view begins. This page ranks suppliers directly — Top 10 and Bottom 10 by performance score, sitting side by side so underperformers are impossible to miss. A Supplier Spend vs. Performance Score scatter plot flags the highest-risk suppliers: the ones who take a large share of spend but score poorly. A treemap breaks down where the procurement budget is actually going by category.

This page answers: *which suppliers and categories need action, and where's the risk concentrated?*

## Page 3 — Operational Performance Dashboard

The quality and delivery layer underneath the numbers. A Monthly On-Time Delivery Trend line tracks whether service levels are improving or slipping. A Procurement Spend by Defect Type donut shows where quality issues are costing the most. A ribbon chart ranks categories by monthly spend, making it easy to see if the spend leaderboard is shifting month to month.

This page answers: *what's driving the scores on the first two pages?*

## Design system

- Custom color palette (navy, teal, emerald, amber, crimson) applied consistently across all three pages, including conditional-formatting shades for status indicators
- Rounded, shadowed KPI cards for a cleaner, modern look rather than default Power BI callouts
- Consistent navy header band with page titles on every page
- Fixed 1280×720 canvas across all pages for uniform export/screenshot sizing

## Skills demonstrated

- Star schema data modeling in Power BI (fact/dimension separation, disconnected measures table)
- DAX measure design for procurement KPIs (spend, on-time delivery, defect rate, composite scoring, lead time)
- Cross-page synced slicers for a consistent filtering experience
- Custom visual theming and KPI card design beyond default templates
- Structuring a report for two audiences (executive summary vs. analyst drill-down) in one deliverable

---

*Note: This is a self-directed portfolio project built to practice end-to-end BI development — data modeling, DAX, and report design — using a synthetic dataset modeled on real-world procurement/supplier scorecard use cases.*
