---
DocID: ERAGS-REQ-IF-001
Title: Interface Requirements between ERAGS and External Subsystems
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-04
LastUpdatedDate: 2025-12-04
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
RelatedDocs:
  - ERAGS-REQ-HL-001
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
RelatedFolders:
  - models/
  - data/
  - qa/
---

# Interface Requirements between ERAGS and External Subsystems

## 1. Purpose

This document defines the high-level interface requirements between ERAGS and other subsystems such as the CMMS/WFM, Asset Inventory & GIS, Finance, HSE and Analytics systems. These interfaces ensure that ERAGS governance processes have access to necessary data and can provide requirements and constraints to other subsystems.

## 2. Interface with CMMS/WFM (Maintenance & Operations Management)

### ERAGS-IF-101 – Performance Data Provision

- **Statement:** The CMMS/WFM subsystem shall provide ERAGS with summarised performance data (availability, MTTR, response times, fault counts) at agreed intervals and levels of aggregation (for example by corridor, area and asset class).  
- **Rationale:** Enables ERAGS to monitor performance and evaluate effectiveness of maintenance strategies.  
- **Verification:** Inspection of data interfaces and example performance reports.

### ERAGS-IF-102 – Programme Feedback

- **Statement:** ERAGS shall provide the CMMS/WFM subsystem with approved annual and multi-year programmes, including priority, scope and target timelines, to support detailed scheduling and execution.  
- **Rationale:** Aligns maintenance and renewal work with governance decisions.  
- **Verification:** Review of communication mechanisms and programme documentation.

## 3. Interface with Asset Inventory & GIS

### ERAGS-IF-201 – Asset Data Access

- **Statement:** The Asset Inventory & GIS subsystem shall allow ERAGS to access asset registers and mapping information necessary for strategy development, risk analysis and programme planning.  
- **Rationale:** Strategy and governance decisions require spatial and attribute data about assets.  
- **Verification:** Inspection of data-access mechanisms and example extracts.

### ERAGS-IF-202 – Asset Data Requirements Provision

- **Statement:** ERAGS shall define and communicate mandatory asset data fields and quality rules to the Asset Inventory & GIS subsystem so that asset records are captured and maintained to governance standards.  
- **Rationale:** Ensures that asset data used in governance is fit for purpose.  
- **Verification:** Review of data specifications and configuration in the Asset Inventory & GIS subsystem.

## 4. Interface with Finance and Energy Billing

### ERAGS-IF-301 – Cost and Energy Data Provision

- **Statement:** The Finance and billing functions shall provide ERAGS with cost and energy data for lighting and signals, aggregated in a way that supports lifecycle and energy-performance analysis.  
- **Rationale:** Governance decisions require understanding of cost and energy impacts.  
- **Verification:** Review of reporting formats and sample financial/energy reports.

### ERAGS-IF-302 – Programme and Budget Alignment

- **Statement:** ERAGS shall provide Finance with clear descriptions of approved programmes, including cost estimates, to support budget planning and expenditure monitoring.  
- **Rationale:** Ensures financial planning aligns with asset governance priorities.  
- **Verification:** Review of budget proposals and monitoring reports.

## 5. Interface with HSE and Incident Management

### ERAGS-IF-401 – Incident Data Provision

- **Statement:** The HSE and incident management subsystems shall provide ERAGS with periodic summaries of incidents and near-misses related to electrical and roadside work.  
- **Rationale:** Governance must consider safety outcomes when updating policies and strategies.  
- **Verification:** Review of incident summary reports and their use in ERAGS reviews.

### ERAGS-IF-402 – Governance Requirements for Safety

- **Statement:** ERAGS shall communicate asset-related safety governance requirements (for example risk tolerances, critical locations) to the HSE subsystem to inform operational safety procedures.  
- **Rationale:** Aligns field-safety practices with governance-level risk decisions.  
- **Verification:** Review of safety procedures and evidence of linkage to ERAGS decisions.

## 6. Interface with Analytics and KPI Reporting

### ERAGS-IF-501 – KPI Definition Provision

- **Statement:** ERAGS shall provide the Analytics subsystem with definitions, formulas and target values for KPIs used in governance.  
- **Rationale:** Ensures that KPIs are calculated consistently and transparently.  
- **Verification:** Review of KPI definition documents and analytics configurations.

### ERAGS-IF-502 – Analytics Feedback Loop

- **Statement:** The Analytics subsystem shall provide ERAGS with periodic KPI dashboards and analytical findings, including trend analyses and risk indicators, to support policy and strategy review.  
- **Rationale:** Creates a feedback loop for continuous improvement.  
- **Verification:** Inspection of dashboards, reports and minutes of governance review meetings.

## 7. Relationship to Models and QA

- `/models` shall define interface diagrams and data-exchange models based on these requirements.  
- `/qa` shall include test cases verifying that interfaces are implemented and functioning as intended.
