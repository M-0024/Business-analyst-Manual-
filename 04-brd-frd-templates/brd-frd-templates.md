# BRD & FRD Templates

Once requirements are gathered and root causes are understood, a BA documents them formally so stakeholders can review, approve, and developers/process owners can build against them. This note covers the two core document types.

## What I'm trying to achieve here
Learn the structure of a BRD and FRD well enough to draft one from scratch for a real process change — this is often the actual deliverable a BA is judged on.

---

## 1. BRD (Business Requirement Document)
Captures the **business need** — what problem is being solved and why, from a business perspective, without technical detail.

**Typical BRD structure:**
- Project/Initiative Name
- Business Objective — why this matters, tied to a business goal
- Background/Problem Statement — the current pain point (this is where RCA findings go)
- Scope — what's in scope and explicitly out of scope
- Stakeholders — who's involved (links to note 03's RACI)
- Business Requirements — numbered list of what the business needs, in plain language
- Assumptions & Constraints
- Success Criteria / KPIs — how success will be measured (links to note 02's KPI section)
- Approval sign-off section

## 2. FRD (Functional Requirement Document)
Translates the BRD into **specific, testable functional requirements** — what the system/process must actually do, in enough detail for developers or process designers to build it.

**Typical FRD structure:**
- Reference to the related BRD
- Functional Requirements — numbered, specific, testable statements (e.g. "System shall auto-populate payment status from SAP HANA field X within 2 seconds of query receipt")
- Process Flow / Workflow diagrams
- Data Requirements — what data is needed, from where
- Business Rules — logic/conditions the system must follow
- Non-Functional Requirements — performance, security, availability expectations
- Acceptance Criteria — conditions that must be met for the requirement to be considered done

## 3. BRD vs FRD — the key difference
BRD answers **"what does the business need and why."** FRD answers **"exactly how will the solution behave to meet that need."** A BRD is written for business stakeholders; an FRD is written so it's unambiguous enough for a technical team to build from.

---

## How I'd apply this in my own work
Draft a BRD for the Germany vendor helpdesk automation idea: Problem Statement (from the case study in note 07), Business Requirements (auto-respond to standard payment-status queries), Success Criteria (reduced response time, reduced query volume to agents). Then break it into an FRD with exact functional rules (which query types trigger automation vs. route to an agent).

## Notes / open questions
- Draft a real BRD for the helpdesk automation case study using this template
- Learn how user stories (Agile format, see note 06) relate to/replace FRDs in Agile teams
