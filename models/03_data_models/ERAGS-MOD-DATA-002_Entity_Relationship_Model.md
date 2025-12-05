---
DocID: ERAGS-MOD-DATA-002
Title: ERAGS Governance Entity Relationship Model
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
  - ERAGS-MOD-DATA-001
  - ERAGS-REQ-DATA-001
  - ERAGS-REQ-IF-001
RelatedFolders:
  - models/04_information_flows/
  - qa/
  - data/
---

# ERAGS Governance Entity Relationship Model

## 1. Purpose

This model describes the conceptual relationships between ERAGS governance data entities defined in `ERAGS-MOD-DATA-001_Governance_Data_Dictionary.md`. It supports:

- Understanding how information flows are grounded in data structures.
- Definition of interfaces with external subsystems (CMMS/WFM, GIS, Finance, HSE, Analytics).
- Design of QA checks to ensure referential integrity and data quality.

## 2. Key Entities

Entities:

- AssetGovernanceRecord
- PerformanceSummary
- KPIRecord
- ProgrammeRecord
- DecisionLogEntry
- IncidentSummary
- EnergyCostSummary
- GovernanceDocumentMetadata

## 3. High-Level Relationships (Narrative)

1. **AssetGovernanceRecord ↔ PerformanceSummary**
   - PerformanceSummary records are aggregated over groups of assets.
   - A PerformanceSummary may aggregate multiple AssetGovernanceRecords based on AggregationLevel and AggregationKey.
   - Relationship: many-to-many via a conceptual grouping, not necessarily stored physically in ERAGS, but definable in analytics/queries.

2. **PerformanceSummary ↔ KPIRecord**
   - KPIRecord often uses PerformanceSummary as input.
   - One PerformanceSummary may feed multiple KPIRecords (different KPIs, scopes).
   - One KPIRecord may be derived from multiple underlying PerformanceSummary records (e.g. across multiple areas).

3. **ProgrammeRecord ↔ AssetGovernanceRecord**
   - A ProgrammeRecord typically targets one or more sets of assets.
   - Relationship: many-to-many, conceptually realised via:
     - Asset selection criteria (e.g. all Poor-condition assets in Area X), or
     - Explicit lists of assets for specific programmes.

4. **ProgrammeRecord ↔ KPIRecord**
   - KPIRecords provide evidence to justify ProgrammeRecords and monitor their impact.
   - Relationship:
     - KPIRecord(s) → motivate ProgrammeRecord (input).
     - Later KPIRecord(s) → measure ProgrammeRecord impact (output).

5. **DecisionLogEntry ↔ GovernanceDocumentMetadata**
   - Decisions refer to one or more documents they relate to (policies, strategies, programmes).
   - GovernanceDocumentMetadata represents those documents.
   - Relationship: many-to-many via DecisionLogEntry.RelatedDocIDs.

6. **DecisionLogEntry ↔ ProgrammeRecord**
   - Some decisions explicitly approve or modify ProgrammeRecord entries.
   - Relationship:
     - Programme decision: DecisionLogEntry links to ProgrammeID in RelatedDocIDs or an additional field if needed.

7. **IncidentSummary ↔ PerformanceSummary**
   - IncidentSummary contributes to understanding performance.
   - For safety-related KPIs, incident counts are an input to KPIRecord via PerformanceSummary or directly.

8. **EnergyCostSummary ↔ PerformanceSummary and KPIRecord**
   - EnergyCostSummary informs energy performance KPIs and cost-effectiveness analyses.
   - Relationship:
     - EnergyCostSummary records may be aligned with PerformanceSummary periods and aggregations.

9. **GovernanceDocumentMetadata ↔ All Governance Artefacts**
   - Each governance document has associated metadata according to this entity.
   - The relationship to other entities is not direct relational keys but semantic links (DocIDs referenced in DecisionLogEntry, programme documentation, etc.).

## 4. Simplified Textual ER Diagram

The relationships can be summarised as:

- `AssetGovernanceRecord` (1..*) ↔ (0..*) `PerformanceSummary`  
  Joined by: AggregationLevel/AggregationKey definitions.

- `PerformanceSummary` (0..*) ↔ (0..*) `KPIRecord`  
  KPIRecord uses PerformanceSummary as input.

- `ProgrammeRecord` (0..*) ↔ (0..*) `AssetGovernanceRecord`  
  Many-to-many through selection criteria or explicit lists.

- `ProgrammeRecord` (0..*) ↔ (0..*) `KPIRecord`  
  KPIs justify programmes and assess results.

- `DecisionLogEntry` (0..*) ↔ (0..*) `ProgrammeRecord`  
  DecisionLogEntry records approvals/changes.

- `DecisionLogEntry` (0..*) ↔ (0..*) `GovernanceDocumentMetadata`  
  Each decision may reference multiple documents.

- `IncidentSummary` (0..*) ↔ (0..*) `PerformanceSummary`  
  Incident summaries aligned to performance periods and areas.

- `EnergyCostSummary` (0..*) ↔ (0..*) `PerformanceSummary`  
  Energy and cost aligned to performance summaries.

## 5. Use in Interfaces and Analytics

- Interface requirements in `ERAGS-REQ-IF-001` describe what data ERAGS expects from CMMS, GIS, Finance, HSE and Analytics.
- This model clarifies:
  - Which entities are predominantly populated from external systems (e.g. PerformanceSummary, EnergyCostSummary, IncidentSummary).
  - Which are created inside ERAGS (e.g. ProgrammeRecord, DecisionLogEntry, KPIRecord).

Analytics workflows and QA scripts can use this ER model to:

- Validate that IDs and keys are consistent across entities.
- Check that every ProgrammeRecord referenced in a decision has a corresponding DecisionLogEntry.
- Verify that KPIRecords used to motivate a programme are consistent with underlying PerformanceSummary and IncidentSummary records.

## 6. Diagram Reference (Optional)

A graphical ER diagram may be created and stored as:

- `models/03_data_models/ERAGS-MOD-DATA-002_Entity_Relationship_Model.png`

This Markdown file should then embed or link that diagram. For now, this narrative model acts as the primary reference.
