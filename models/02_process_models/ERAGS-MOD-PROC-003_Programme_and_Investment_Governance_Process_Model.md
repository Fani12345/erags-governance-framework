---
DocID: ERAGS-MOD-PROC-003
Title: Programme and Investment Governance Process Model
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-05
LastUpdatedDate: 2025-12-05
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
RelatedDocs:
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-REQ-HL-001
  - ERAGS-REQ-DATA-001
  - ERAGS-REQ-IF-001
RelatedFolders:
  - requirements/
  - models/03_data_models/
  - models/04_information_flows/
  - processes/
  - qa/
---

# Programme and Investment Governance Process Model

## 1. Purpose

This model describes how ERAGS develops, evaluates, prioritises and approves annual and multi-year programmes and investment plans for road-lighting and traffic-signal assets.

It operationalises requirement ERAGS-F-006 (Programme and Investment Governance) and connects strategy, data and performance into funding and work decisions.

## 2. Scope

The process covers:

- Translation of Asset Strategy into candidate programmes.
- Evaluation of candidate programmes using technical, financial and risk criteria.
- Prioritisation under budget constraints.
- Approval and communication of final programmes to operational subsystems (CMMS/WFM, Finance, Projects).

It does not cover detailed project-level design or construction management.

## 3. Inputs and Outputs

### 3.1 Inputs

- Asset Strategy (ERAGS-DOC-STR-001).
- Asset and condition data (from Asset Inventory & GIS).
- Performance and fault data (from CMMS/WFM, Analytics).
- Energy and cost data (from Finance and energy management).
- Incident and safety data (from HSE).
- Available and projected budgets and resource constraints.
- Regulatory and policy requirements (for example mandated service levels).

### 3.2 Outputs

- Multi-year programme proposals (for example 3–5 years) with prioritised projects.
- Approved annual programmes with defined scopes and indicative budgets.
- Structured input to CMMS/WFM for implementation planning.
- Feedback and justification documents for Finance and Executive Management.

## 4. Roles and Components

### 4.1 Roles

- Strategy Lead (often same person as Policy Owner or designated engineer).
- Data and Analytics Liaison.
- Finance Representative.
- HSE Representative.
- Executive Approver or Programme Board.

### 4.2 ERAGS Components Involved

- Strategy Management Component (primary).
- Performance and KPI Management Component.
- Data and Information Integration Component.
- Governance Process Management Component.
- Document and Configuration Management Component.
- Analytics and Insights Interface Component.

## 5. Programme Governance Flow (Nominal Case)

1. **Initiate Programme Planning Cycle**
   - Triggered annually (or as defined in governance calendar).
   - Governance Process Management Component initiates programme cycle and defines timeline.

2. **Confirm Strategic Objectives and Constraints**
   - Strategy Management Component:
     - Reviews Asset Strategy and key objectives (safety, reliability, energy savings, equity).
     - Confirms budget envelopes and policy constraints with Finance and Executive Management.

3. **Compile Candidate Needs and Options**
   - Data and Information Integration Component aggregates:
     - Asset needs (for example age, condition, criticality).
     - Performance issues (for example low availability corridors, frequent faults).
     - Safety and incident hotspots.
     - Energy inefficiencies.
   - Strategy Management Component develops candidate programme options (for example bulk LED retrofit, targeted signal upgrades, feeder rebuilds).

4. **Define Evaluation Criteria and Weightings**
   - Evaluation criteria agreed (for example safety impact, reliability impact, cost-effectiveness, energy savings, social impact).
   - Weightings and scoring scales documented.

5. **Evaluate Candidate Programmes**
   - Each candidate programme is scored against criteria using:
     - KPI data.
     - Forecast models.
     - Cost and benefit estimates.
   - Analytics and Insights Interface Component may support scenario analysis.

6. **Prioritise and Assemble Draft Programme**
   - Programmes are ranked based on scores and strategic fit.
   - Draft multi-year plan is assembled within budget constraints:
     - Identify which programmes are in Year 1, Year 2, etc.
     - Identify deferrals or alternative options.

7. **Risk and Feasibility Review**
   - HSE and operational stakeholders review draft programme for:
     - Implementation risk.
     - Safety implications.
     - Resource feasibility (skills, equipment, time).
   - Adjustments made as needed.

8. **Approval**
   - Draft programme is submitted to Executive Approver or Programme Board.
   - Decisions recorded:
     - Approved programme.
     - Conditions or changes required.
     - Deferred items and rationale.

9. **Documentation and Baseline**
   - Document and Configuration Management Component:
     - Finalises programme documentation (scope, budgets, priorities).
     - Establishes a programme baseline (version and, if appropriate, Git tag for the governance repo).
   - Links programme records to relevant strategy and requirements entries in the RTM.

10. **Communication and Handover**
    - Approved programme details provided to:
      - CMMS/WFM for work planning and project set-up.
      - Finance for budgeting and monitoring.
      - Other stakeholders as required.
    - Any constraints or key assumptions are documented and communicated.

11. **Monitoring and Feedback**
    - Performance and KPI Management Component:
      - Monitors programme delivery against KPIs and milestones.
      - Feeds actual outcomes back into strategy and future programme cycles.

## 6. Alternate and Exception Paths

- **Mid-Cycle Adjustments**
  - If major changes occur (for example budget cuts, emergency works):
    - Strategy Management Component initiates a mini-cycle focused on re-prioritisation.
    - Steps 3–8 are applied at a reduced scope and accelerated schedule.

- **Pilot or Experimental Programmes**
  - For innovative technologies or approaches:
    - A smaller pilot programme may be run.
    - Results are explicitly captured for use in future evaluation cycles.

## 7. Mapping to Requirements and RTM

This process model supports and implements, among others:

- ERAGS-F-002 – Asset Strategy.
- ERAGS-F-006 – Programme and Investment Governance.
- ERAGS-F-008 – Performance and KPI Management (through link to performance data).
- ERAGS-D-001, ERAGS-D-002 – Asset and performance data use.
- ERAGS-IF-101, ERAGS-IF-201, ERAGS-IF-301, ERAGS-IF-501 – Interfaces with CMMS/WFM, GIS, Finance and Analytics.

In `ERAGS_RTM.csv`, this document should be referenced as an `Implementing_Document_or_Process` for these requirement IDs and any derived programme-governance requirements.

