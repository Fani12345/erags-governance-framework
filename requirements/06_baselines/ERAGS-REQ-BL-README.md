---
DocID: ERAGS-REQ-BL-README
Title: Requirements Baselines for ERAGS
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
  - ERAGS-REQ-CH-LOG
  - ERAGS-REQ-HL-001
RelatedFolders:
  - 01_high_level/
  - 02_derived/
---

# Requirements Baselines for ERAGS

## 1. Purpose

This document explains how requirements baselines for ERAGS are recorded in this folder. Baselines provide stable snapshots of requirements and the RTM at key points in time (for example before major design phases or reviews).

## 2. Baseline Structure

For each baseline, a subfolder may be created with the baseline name, for example:

- `v0.1-ERAGS-REQ/`
- `v0.2-ERAGS-REQ/`

A baseline folder typically contains:

- A copy of `01_high_level/ERAGS-REQ-HL-001_High_Level_Requirements.md` at the time of baseline.
- Relevant derived requirements from `02_derived/`.
- A copy of `ERAGS_RTM.csv` at the time of baseline.
- Optional change summary or release notes.

## 3. Relationship to Git Tags

Where appropriate:

- A Git tag shall be created with the same name as the baseline folder (for example `v0.1-ERAGS-REQ`).
- The tag and the folder together allow reconstruction of the exact state of requirements and related artefacts.

## 4. Use

Baselines shall be created:

- At initial approval of the requirements for ERAGS (for example `v0.1-ERAGS-REQ`).
- Before major design, procurement or implementation phases.
- After significant changes triggered by regulation, organisational changes or major performance issues.

Baselines shall be referenced in the change log (`ERAGS-REQ-CH-LOG.md`) and in governance meeting records where relevant.
