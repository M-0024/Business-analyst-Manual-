# Root Cause Analysis & Statistical Techniques for BA

Once requirements are gathered, a BA needs to understand *why* a problem is happening before proposing a solution. This note covers root cause analysis (RCA) methods, statistical techniques, and — since this is where I work day-to-day — invoice/AP-specific analysis techniques.

## What I'm trying to achieve here
Move from "what does the stakeholder want" (requirements gathering) to "what is actually causing the problem, and how do I prove it with data" — this is the analytical core of the BA role, and where SQL/Excel/Power BI skills get used directly.

---

## Part 1: Root Cause Analysis (RCA) Techniques

**1. 5 Whys**
Ask "why" repeatedly (usually 5 times) until you reach the underlying cause instead of the symptom.
*Example:* Invoice is on hold → Why? PO mismatch → Why? Vendor used wrong PO number → Why? Vendor wasn't given updated PO format → Why? No process to notify vendors of PO format changes.

**2. Pareto Analysis (80/20 Rule)**
80% of problems typically come from 20% of causes. Used to prioritize which root causes to fix first by ranking causes by frequency/impact.
*BA use:* Rank invoice hold reasons by volume — fix the top few causing most of the holds before chasing rare edge cases.

**3. Fishbone / Ishikawa Diagram**
Groups potential causes into categories (People, Process, Systems, Data, Environment) branching off a central problem. Useful when a problem has multiple contributing causes across different areas.

**4. Fault Tree Analysis**
Works backward from a failure/problem, mapping the logical combinations of events that could cause it. More rigorous than 5 Whys — used when a failure could stem from several combined causes.

**5. Bottleneck Analysis**
Identifies the single slowest step in a process that limits overall throughput (the "constraint"). Fixing anything other than the actual bottleneck doesn't speed up the whole process — a core idea from Theory of Constraints.
*BA use:* In invoice processing, mapping time spent at each stage (receipt → data entry → approval → payment) to find which single stage is holding up the whole cycle, rather than assuming.

**6. Value Stream / Process Mining**
Maps every step an invoice (or any item) actually goes through, including delays and rework loops, often using real system timestamp data rather than the "official" process on paper. Reveals hidden bottlenecks and rework that people don't report.

---

## Part 2: Statistical & Analytical Techniques for BA

**1. Descriptive Statistics**
Mean, median, mode, standard deviation, min/max — used to summarize a dataset (e.g. average invoice hold duration) before drawing conclusions.

**2. Variation Analysis**
Looking beyond the average to see how spread out the data is — standard deviation, variance, and coefficient of variation (std dev ÷ mean, useful for comparing variability across metrics with different scales).
*BA use:* Two vendors might have the same average payment delay, but one is consistently a few days late while the other swings wildly — variation analysis tells them apart, and the second is usually the bigger process risk.

**3. Trend Analysis**
Looking at a metric over time (e.g. monthly invoice hold volume) to spot patterns, seasonality, or whether a process change actually improved things.

**4. Correlation Analysis**
Checking whether two variables move together (e.g. does hold volume correlate with vendor onboarding volume, or with month-end volume spikes?). Correlation isn't causation — it points toward a hypothesis to test further, not a proven cause.

**5. Regression Analysis**
Goes a step past correlation — models the relationship between one variable and one or more others to estimate impact and, to some extent, predict outcomes.
*BA use:* Estimating how much invoice value or vendor count predicts processing time, to help forecast workload as volume grows (e.g. with Germany onboarding).

**6. Control Charts**
Shows whether a process is stable ("in control") or has unusual variation over time — flags when something has genuinely changed vs. normal day-to-day fluctuation.

**7. Hypothesis Testing (basic)**
A structured way to check if an observed difference (e.g. hold rate before vs. after a process change) is statistically meaningful or just random noise.

---

## Part 3: Invoice / AP-Specific Analysis

**1. Invoice-Level Analysis**
Examining individual invoices (or invoice segments) in detail — by vendor, amount band, PO vs. non-PO, exception type — to spot patterns that aggregate numbers hide.

**2. Payment Cycle Analysis**
Breaking the payment process into stages (invoice receipt → validation → approval → payment release) and measuring time spent at each stage, to see where delays actually accumulate.

**3. Average Invoice Lifecycle / Turnaround Time (TAT) Analysis**
Measuring the average time from invoice receipt to final payment (or to hold resolution), often segmented by vendor, region, or invoice type, to track efficiency and spot outliers.

**4. KPI Analysis**
Tracking standard AP performance indicators over time, such as:
- **DPO (Days Payable Outstanding)** — average time taken to pay invoices
- **Touchless/straight-through processing rate** — % of invoices processed with no manual intervention
- **First-time match rate** — % of invoices matching PO/GR with no exception
- **Hold rate** — % of invoices landing on hold, and by which reason
- **Cost per invoice processed**
- **Exception aging** — how long unresolved exceptions sit before resolution

---

## How I'd apply this in my own work
- Use bottleneck analysis on the Germany invoice cycle to find the true slowest stage, not the most complained-about one
- Use variation analysis (not just averages) when comparing vendor payment delays
- Track touchless processing rate and hold rate as core KPIs when proposing the helpdesk automation idea, to measure real impact
- Use Pareto + invoice-level analysis together: rank hold reasons, then drill into invoice-level detail for the top 2–3

## Notes / open questions
- Build a Pareto chart + payment cycle stage-time chart in Power BI using my synthetic AP dataset
- Try a real bottleneck analysis on one process I know well, using actual stage timestamps
- Practice a simple regression (e.g. invoice volume vs. processing time) once I have enough synthetic data

---

## Part 4: Additional Analysis Techniques (Deeper BA Toolkit)

**1. Gap Analysis**
Compares current state ("as-is") to desired future state ("to-be") to identify exactly what's missing — the foundation for scoping a solution once root causes are known.

**2. Cost-Benefit Analysis (CBA) / ROI Analysis**
Weighs the expected cost of a solution against its expected benefit (time saved, error reduction, cost avoided) to justify whether a fix is worth implementing. Every BA proposal eventually needs this to get stakeholder sign-off.

**3. SWOT Analysis**
Strengths, Weaknesses, Opportunities, Threats — a structured way to evaluate a process, team, or proposed solution before committing to it.

**4. Forecasting (Moving Average / Exponential Smoothing)**
Projecting future values (e.g. next quarter's invoice volume) based on historical trend data. Moving average smooths out noise; exponential smoothing weights recent data more heavily — useful for capacity planning around volume growth (e.g. Germany onboarding).

**5. Outlier Detection (Z-score / IQR)**
Statistical methods to flag data points that are abnormally far from the norm — e.g. an invoice held for 90 days when the average is 5. Important because averages alone can hide these extreme cases.

**6. Segmentation / ABC Analysis**
Grouping data into tiers by impact — e.g. classifying vendors into A (high value/volume, needs close monitoring), B (moderate), C (low, minimal oversight). Helps prioritize where analysis and process attention should focus.

**7. Six Sigma DMAIC Framework**
A structured problem-solving cycle: **D**efine the problem → **M**easure current performance → **A**nalyze root causes (this is where 5 Whys/Pareto/Fishbone plug in) → **I**mprove by implementing a fix → **C**ontrol by monitoring to sustain the improvement. Useful as an overall framework tying together everything in Parts 1–3.

**8. Process Capability (Cp/Cpk)**
A Six Sigma measure of how consistently a process stays within an acceptable range (e.g. invoices processed within SLA). Tells you not just the average performance but how reliably the process meets a target.

**9. Benchmarking**
Comparing your process metrics (e.g. DPO, touchless rate) against industry standards or other regions/entities within the same company, to judge whether performance is actually good or just "normal for us."

**10. Sensitivity / What-If Analysis**
Testing how an outcome changes when one input variable changes (e.g. "what happens to processing time if invoice volume grows 20%?"). Common in Excel using data tables or scenario manager.

**11. Confidence Intervals**
A range around an estimate (e.g. average TAT) that expresses how certain you are about it, given the sample size — useful to avoid over-trusting a metric based on too little data.

## Updated notes / open questions
- Try Cost-Benefit Analysis on the helpdesk automation idea to justify it in stakeholder terms
- Practice ABC vendor segmentation on the synthetic AP dataset
- Learn DMAIC as the umbrella framework that ties RCA + stats + solution + monitoring together
