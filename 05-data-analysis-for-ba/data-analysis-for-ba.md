# Data Analysis for BA (SQL, Power BI, Excel)

A modern BA is expected to back up findings with real data, not just stakeholder opinions. This note is about how the technical tools I already use (SQL, Power BI, Excel) map onto the BA workflow.

## What I'm trying to achieve here
Connect my existing technical skills to the BA lifecycle explicitly, so I can talk about them as BA capabilities in interviews — not just "I know SQL," but "I use SQL to validate root causes and quantify requirements."

---

## 1. SQL for BA
- Querying transactional data (e.g. invoice tables) to validate a stakeholder's claim before writing it into a BRD as fact
- Building aggregate views (hold volume by reason, by vendor, by month) to support Pareto and trend analysis
- Joining tables (invoice, vendor, PO) to trace root cause across systems — e.g. confirming a PO mismatch pattern by vendor

## 2. Power BI for BA
- Turning analysis (Pareto charts, trend lines, KPI tracking) into a dashboard stakeholders can self-serve, instead of a one-time static report
- Drill-throughs let a stakeholder go from a summary KPI (e.g. hold rate) down to invoice-level detail — directly supports the invoice-level analysis from note 02
- Useful for presenting before/after comparisons when proposing or validating a process change

## 3. Excel for BA
- Fast, flexible analysis when a full dashboard isn't needed yet — pivot tables for quick Pareto/frequency analysis
- What-if analysis (data tables, scenario manager) — directly ties to the sensitivity analysis technique in note 02
- Often the fastest way to build a rough BRD success-metric baseline before formal reporting exists

## 4. Choosing the right tool
- **SQL** — when I need to go to the source data directly, especially for large volumes or repeatable queries
- **Power BI** — when the output needs to be shared, updated regularly, and self-service for stakeholders
- **Excel** — for fast, one-off analysis, prototyping a metric, or when stakeholders expect a spreadsheet format

---

## How I'd apply this in my own work
Use SQL to pull and validate hold-reason data → Excel for a first-pass Pareto chart while exploring → Power BI for the final dashboard once the analysis is proven, so Germany stakeholders can track hold trends themselves.

## Notes / open questions
- Practice writing a SQL query specifically to validate a root-cause hypothesis (not just report numbers)
- Build one Power BI page that mirrors a KPI list from note 02 (DPO, hold rate, touchless rate)
