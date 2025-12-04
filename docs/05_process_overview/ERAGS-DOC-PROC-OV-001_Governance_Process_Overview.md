---
DocID: ERAGS-DOC-PROC-OV-001
Title: Governance Process Overview for ERAGS
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
  - ERAGS-DOC-OV-000
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-STK-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-REF-001
RelatedFolders:
  - processes/
  - requirements/
  - models/
  - qa/
---

# Governance Process Overview for ERAGS

## 1. Purpose

This document provides an overview of the key governance processes that make up the Electrical Roads Asset Governance & Strategy System (ERAGS). It describes the main workflows that ensure policies, strategies and major asset decisions are controlled, transparent and traceable.

## 2. Process Architecture

At a high level, ERAGS governance consists of the following core processes:

1. **Context and Stakeholder Review** – maintain up-to-date understanding of context, drivers and stakeholders.
2. **Policy Management** – create, review and approve the Asset Management Policy and related policies.
3. **Asset Strategy Management** – develop and maintain the Lighting and Signals Asset Strategy.
4. **Requirements and Performance Management** – define and maintain performance and data requirements.
5. **Programme and Investment Governance** – develop and approve annual and multi-year asset programmes.
6. **Change Control for Standards and Technologies** – manage changes in technical standards and technology choices.
7. **Review, Audit and Continuous Improvement** – periodically assess the effectiveness of ERAGS and drive improvements.

Detailed descriptions of each process will be documented in the `/processes` folder, using the roles defined in ERAGS-DOC-STK-001.

## 3. Core Governance Processes

### 3.1 Context and Stakeholder Review

**Objective:** Ensure that ERAGS remains aligned with legal, organisational, technical and stakeholder context.

**Key Activities:**

- Periodic review of:
  - Laws, regulations and standards relevant to road lighting, traffic signals and electrical safety.
  - Organisational strategies and risk appetite.
  - Stakeholder expectations and feedback.
- Updating ERAGS-DOC-CTX-001 and ERAGS-DOC-STK-001 as needed.
- Communicating significant contextual changes to policy, strategy and operational owners.

**Typical Frequency:** Annual review, or as triggered by major changes.

### 3.2 Policy Management

**Objective:** Maintain a current, approved Asset Management Policy and related governance policies.

**Key Activities:**

- Initiation of policy creation or revision (triggered by context changes or scheduled review).
- Drafting policy text by the Electrical Engineer or designated working group.
- Consultation with internal and external stakeholders.
- Formal review and approval by the Director – Roads Network Maintenance and, where required, higher-level management.
- Publication and communication to relevant units, including operations and contractors.

**Outputs:**

- Approved version of ERAGS-DOC-POL-001 and any related policies.
- Record of reviews, comments and approvals.

### 3.3 Asset Strategy Management

**Objective:** Maintain a documented, justifiable Lighting and Signals Asset Strategy aligned with the Policy.

**Key Activities:**

- Collate asset data, performance information and risk assessments.
- Analyse options for lifecycle strategies and programmes.
- Draft and update ERAGS-DOC-STR-001.
- Align strategy with available funding and organisational priorities.
- Obtain approvals through appropriate governance forums.

**Outputs:**

- Approved asset strategy document and any supporting models.
- Documented rationale for major strategic directions.

### 3.4 Requirements and Performance Management

**Objective:** Define and keep current the high-level requirements and performance targets for electrical road assets.

**Key Activities:**

- Draft and maintain the ERAGS High-Level Requirements Specification in `/requirements`.
- Define and review performance targets and KPIs in collaboration with stakeholders.
- Ensure that requirements link to context, policy and strategy documents.
- Maintain the Requirements Traceability Matrix (RTM) to link requirements to processes and data.

**Outputs:**

- Updated requirements documentation and RTM.
- Documented KPI definitions and targets.

### 3.5 Programme and Investment Governance

**Objective:** Ensure that annual and multi-year programmes of work for lighting and signals are consistent with policy, strategy and risk.

**Key Activities:**

- Translate strategy into candidate programmes and projects.
- Evaluate options using risk, performance and cost information.
- Prioritise programmes within funding constraints.
- Submit programme proposals to funding authorities and management.
- Record approvals, conditions and variations.

**Outputs:**

- Approved annual and multi-year programmes.
- Traceable records linking programmes to policy, strategy, requirements and data.

### 3.6 Change Control for Standards and Technologies

**Objective:** Control changes to technical standards, approved equipment types and technology platforms.

**Key Activities:**

- Receive and record proposals for changes to standards or equipment.
- Assess impacts on safety, compatibility, maintainability, lifecycle cost and data requirements.
- Where appropriate, define and execute pilots or trials.
- Make and document decisions through constituted governance forums.
- Update standards, specifications and related requirements.

**Outputs:**

- Approved or rejected change records.
- Updated technical standards and specifications.
- Updated models and requirements when needed.

### 3.7 Review, Audit and Continuous Improvement

**Objective:** Confirm that ERAGS is operating as intended and identify opportunities for improvement.

**Key Activities:**

- Periodic review of performance results and KPIs.
- Internal audits of governance processes, traceability and compliance.
- Follow-up on audit findings and lessons learned from incidents or projects.
- Update policies, strategies, requirements and processes to reflect improvements.

**Outputs:**

- Audit and review reports.
- Improvement actions with owners and due dates.
- Updated ERAGS documents and models.

## 4. Relationships to Other Artefacts

- Each governance process will be documented as a detailed process description in the `/processes` folder, using the generic process template.
- Requirements in `/requirements` will reference these processes where relevant.
- Models in `/models` will represent the process architecture and data flows that support these processes.
- QA plans and test scenarios in `/qa` will verify that the processes are implemented and traceable to requirements.

## 5. Governance of ERAGS Itself

The ERAGS governance processes are themselves subject to:

- Version control and change management as described in Section 3.6.
- Periodic review and audit as described in Section 3.7.
- Documentation control practices (unique IDs, versioning, metadata and relationships) as applied across all ERAGS documents.
