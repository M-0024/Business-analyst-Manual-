# Case Study: Germany Vendor Helpdesk Automation

A real requirements-and-process problem from my AP/P2P role, written up as a BA case study — showing the full BA lifecycle from problem discovery to proposed solution.

## Background
On the Germany AP account, a large share of vendor helpdesk queries are repetitive payment-status requests — vendors asking "where is my invoice/payment," which is answerable directly from SAP HANA data but currently requires manual lookup and reply for every query.

## 1. Problem Identification
- High volume of repetitive, low-complexity queries consuming helpdesk time
- Manual lookups slow down response time and take capacity away from higher-value invoice processing work
- Vendor experience suffers from response delays on a question that has a deterministic answer

## 2. Requirements Elicitation
- **Document analysis**: reviewed recurring query patterns and payment-status lookup steps in SAP HANA
- **Process observation**: mapped the manual steps a helpdesk agent takes today to answer a payment-status query

## 3. As-Is Process
Vendor emails/calls → Agent manually looks up invoice in SAP HANA → Agent drafts and sends response → Query closed.

## 4. Proposed To-Be Process
Vendor query received → Automated lookup pulls payment status from SAP HANA → Templated response auto-generated and sent (or routed to agent only for exceptions) → Query closed.

## 5. Proposed Solution
A Power Automate-based lean workflow that intercepts standard payment-status queries, pulls status directly from SAP HANA, and auto-populates a response — reserving agent time for exceptions and non-standard queries.

## 6. Expected Business Impact
- Reduced average response time on payment-status queries
- Freed-up helpdesk capacity for invoice processing and complex vendor issues
- More consistent, standardized vendor communication

## BA Skills Demonstrated
Requirements elicitation, as-is/to-be process mapping, stakeholder-facing problem framing, and translating an operational pain point into a scoped solution proposal.
