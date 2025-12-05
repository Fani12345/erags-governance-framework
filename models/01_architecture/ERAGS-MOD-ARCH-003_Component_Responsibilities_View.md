---
DocID: ERAGS-MOD-ARCH-003
Title: ERAGS Component Responsibilities View
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
  - ERAGS-MOD-ARCH-002
  - ERAGS-REQ-HL-001
RelatedFolders:
  - requirements/
  - processes/
  - qa/
---

# ERAGS Component Responsibilities View

## 1. Purpose

This document provides a structured view of the responsibilities, inputs and outputs of each logical component in ERAGS. It expands the logical architecture defined in ERAGS-MOD-ARCH-002 into a tabular form that can be used directly by process designers and reviewers.

## 2. Component Responsibility Table

| Component Name                            | Key Responsibilities                                                                                                     | Primary Inputs                                                                                          | Primary Outputs                                                                                           | Key Requirement IDs Implemented                            |
|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| Policy Management Component               | Maintain Asset Management Policy and related policies; manage policy lifecycle (draft, review, approve, publish).       | Context data, stakeholder expectations, regulatory changes, performance insights, incident summaries.   | Updated policy documents, policy change proposals, policy review records.                                | ERAGS-F-001, ERAGS-F-003, ERAGS-R-001, ERAGS-R-002        |
| Strategy Management Component             | Maintain Asset Strategy, develop lifecycle strategies and programmes, align with policy and performance data.          | Approved policies, asset and performance data, risk analyses, resource constraints.                     | Updated Asset Strategy, candidate programmes and prioritisation proposals.                               | ERAGS-F-002, ERAGS-F-006, ERAGS-D-001, ERAGS-D-002        |
| Requirements and Traceability Management  | Maintain high-level and derived requirements, RTM and traceability across ERAGS artefacts.                             | Context, policies, strategy, stakeholder roles, regulatory requirements.                               | Requirements specifications, RTM updates, traceability reports.                                          | ERAGS-F-005, ERAGS-NF-002, ERAGS-D-004, ERAGS-R-003       |
| Governance Process Management             | Define, maintain and monitor governance processes (context review, policy review, programme approval, change control). | Requirements for governance behaviour, existing process descriptions, performance feedback.             | Detailed process descriptions, process performance indicators and improvement proposals.                 | ERAGS-F-003, ERAGS-NF-006, ERAGS-R-003                     |
| Performance and KPI Management            | Define KPIs and targets, coordinate performance data collection, detect deviations and trigger governance actions.     | KPI definitions from requirements, performance data from Analytics and operational systems.            | KPI target sets, performance dashboards (via Analytics), triggers for policy/strategy/process reviews.   | ERAGS-F-008, ERAGS-D-002, ERAGS-NF-006                    |
| Data and Information Integration          | Define governance-level data definitions and interfaces; ensure data quality for governance decisions.                 | Data requirements, external system capabilities (CMMS, GIS, Finance, HSE), data-quality results.       | Data dictionaries, interface specifications, data-quality rules and improvement recommendations.         | ERAGS-D-001, ERAGS-D-002, ERAGS-D-003, ERAGS-IF-201..502  |
| Document and Configuration Management     | Enforce metadata standards and version control; manage baselines and configuration items.                              | Governance documents and models, change requests, baseline decisions.                                  | Document metadata conventions, configuration item lists, baseline records and change-control evidence.   | ERAGS-F-009, ERAGS-D-004, ERAGS-R-003, ERAGS-NF-003       |
| Analytics and Insights Interface          | Specify KPI calculations and reporting needs; receive and interpret analytical outputs.                                | KPI definitions, governance questions, data summaries from Analytics subsystem.                        | KPI calculation specifications, analytical requirements, interpreted insights for policy and strategy.   | ERAGS-F-008, ERAGS-IF-501, ERAGS-IF-502, ERAGS-NF-001     |

## 3. Use by Process Designers

Process designers can use this table to:

- Assign clear component responsibility for each step in governance processes.
- Ensure that each process has defined inputs and outputs compatible with the data models.
- Confirm that each governance activity is supported by at least one logical component.

For example:

- A “Programme Approval” process step that evaluates options and prepares recommendations will primarily involve:
  - Strategy Management Component.
  - Data and Information Integration Component.
  - Performance and KPI Management Component.

## 4. Traceability to Requirements and RTM

For each component, the `Key Requirement IDs Implemented` column:

- Identifies the primary requirements that the component helps satisfy.
- Provides a direct mapping into `requirements/ERAGS_RTM.csv`, where this model file should appear as an `Implementing_Document_or_Process` for those IDs.

As the architecture evolves:

- New requirement IDs may be added to this table.
- Components and responsibilities may be refined, with updates logged via the ERAGS requirements change log.

## 5. Relationship to Other Models

This responsibilities view is directly connected to:

- **ERAGS-MOD-ARCH-002** – which defines the existence and high-level structure of each component.
- **Process models in `models/02_process_models/`** – which use component names when describing who or what executes each process step.
- **Data models in `models/03_data_models/`** – which represent the information each component uses and produces.
- **Flow models in `models/04_information_flows/`** – which show how information moves between these components and external systems.
