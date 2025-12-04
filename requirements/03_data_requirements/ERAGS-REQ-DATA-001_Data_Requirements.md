---
DocID: ERAGS-REQ-DATA-001
Title: Data and Metadata Requirements for ERAGS
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
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-REF-001
RelatedFolders:
  - models/
  - qa/
  - data/
---

# Data and Metadata Requirements for ERAGS

## 1. Purpose

This document elaborates the data-related high-level requirements in ERAGS-REQ-HL-001 into detailed requirements on asset data, performance data, document metadata and data-quality practices that support governance and strategy.

## 2. Asset Data Requirements

### ERAGS-D-101 – Asset Identity and Location

- **Derived From:** ERAGS-D-001  
- **Statement:** Each governance-relevant asset record (lighting, signal, associated facility) shall include a unique identifier, asset class, ownership, and geo-referenced location (coordinates and reference to the road network).  
- **Rationale:** Enables unambiguous referencing and spatial analysis of asset condition and performance.  
- **Verification:** Inspection of data dictionary and sample asset records.

### ERAGS-D-102 – Asset Lifecycle Attributes

- **Derived From:** ERAGS-D-001  
- **Statement:** Asset records shall include lifecycle attributes such as installation date (or best estimate), current condition rating (qualitative or quantitative), and criticality classification.  
- **Rationale:** Provides the necessary information for lifecycle planning, risk assessment and prioritisation.  
- **Verification:** Review of data dictionary and model definitions; inspection of asset records.

## 3. Performance Data Requirements

### ERAGS-D-201 – Fault and Work-Order Data

- **Derived From:** ERAGS-D-002  
- **Statement:** Governance-relevant performance data shall include fault and work-order records with attributes such as fault type, date/time logged, response category, date/time attended, root cause (where determined) and outcome status.  
- **Rationale:** Supports calculation of availability, mean time to repair and response-time compliance.  
- **Verification:** Review of data specification and CMMS/WFM configuration; inspection of example reports.

### ERAGS-D-202 – Energy and Cost Data

- **Derived From:** ERAGS-D-002  
- **Statement:** Governance-relevant performance data shall include energy consumption and cost data for lighting and signals at an appropriate aggregation level (for example feeder pillar, route, area), with identifiable tariff structures.  
- **Rationale:** Enables analysis of energy performance, cost trends and benefits of efficiency projects.  
- **Verification:** Review of energy-data specification and example billing/reconciliation reports.

## 4. Document Metadata Requirements

### ERAGS-D-301 – Governance Document Metadata Fields

- **Derived From:** ERAGS-D-004  
- **Statement:** Each ERAGS governance document shall include, at minimum, the following metadata fields: DocID, Title, Version, Status, OwnerRole, OwnerName, ApproverRole, ApproverName, CreatedDate, LastUpdatedDate, System, RelatedDocs and RelatedFolders.  
- **Rationale:** Supports configuration management, impact analysis and navigation of relationships.  
- **Verification:** Inspection of document headers in `/docs` and `/requirements`.

### ERAGS-D-302 – Document Relationship Recording

- **Derived From:** ERAGS-D-004  
- **Statement:** Governance documents shall use the RelatedDocs and RelatedFolders metadata fields to explicitly record their primary dependencies and outputs within the ERAGS repository.  
- **Rationale:** Provides an explicit map of inter-document relationships for traceability and change impact analysis.  
- **Verification:** Review of document metadata and the document map in `docs/index.md`.

## 5. Data-Quality Requirements

### ERAGS-D-401 – Data Completeness Targets

- **Derived From:** ERAGS-D-003  
- **Statement:** ERAGS shall define minimum completeness targets (for example ≥ 98%) for mandatory fields in asset and performance data used for governance decisions and shall monitor adherence to these targets.  
- **Rationale:** Ensures enough information is available to support robust decisions.  
- **Verification:** Review of data-quality plan and results of completeness checks.

### ERAGS-D-402 – Data Consistency and Validity Checks

- **Derived From:** ERAGS-D-003  
- **Statement:** ERAGS shall define consistency and validity checks (for example ID uniqueness, value ranges, coordinate bounds) and apply them periodically to governance-relevant datasets.  
- **Rationale:** Detects data anomalies that could distort analysis and decisions.  
- **Verification:** Inspection of data-quality procedures and evidence of checks in `/qa`.

### ERAGS-D-403 – Data Timeliness Requirements

- **Derived From:** ERAGS-D-003  
- **Statement:** ERAGS shall define maximum acceptable delays for updating asset and performance data in governance reports (for example faults and work history updated within X days, energy and cost data reconciled monthly).  
- **Rationale:** Ensures governance decisions are based on up-to-date information.  
- **Verification:** Review of data timeliness definitions and monitoring records.

## 6. Relationship to Models, QA and Data

- `/models` shall contain data dictionaries and schemas that implement the requirements defined in this document.  
- `/qa` shall contain data-quality checks and test scenarios linked to the requirement IDs above.  
- `/data` may contain example datasets used to test and demonstrate compliance with these requirements.
