---
DocID: ERAGS-DOC-STR-001
Title: Lighting and Signals Asset Strategy
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
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-REF-001
RelatedFolders:
  - requirements/
  - models/
  - data/
  - qa/
---

# Lighting and Signals Asset Strategy

## 1. Purpose

The purpose of this Asset Strategy is to translate the Asset Management Policy (ERAGS-DOC-POL-001) into concrete lifecycle strategies for road-lighting, traffic-signal and associated electrical assets. It provides direction on how assets will be planned, maintained, renewed and improved over the medium to long term.

## 2. Asset Classes and Criticality

### 2.1 Asset Classes

This Strategy covers the following asset classes:

- **Street-lighting assets**
  - Columns, brackets and foundations
  - Luminaires (including lamps, drivers and optical systems)
  - Feeder pillars, distribution boards and circuit wiring
  - Control devices (photocells, time switches, CMS nodes)
- **Traffic-signal assets**
  - Signal heads and lanterns
  - Local controllers and conflict monitors
  - Detection systems (loops, radar, cameras, push-buttons)
  - Communication devices and cables
  - UPS units and cabinets
- **Associated facilities**
  - Junction boxes, cable ducts and joints
  - Control cabinets for other roadside electrical equipment

### 2.2 Criticality

Asset classes and specific locations differ in their criticality. This Strategy recognises:

- High-criticality assets:  
  - Traffic signals at complex or high-speed intersections.  
  - Lighting at high-risk locations (for example pedestrian crossings, high-crime areas, interchanges).
- Medium-criticality assets:  
  - Arterial-road lighting and standard intersections.
- Lower-criticality assets:  
  - Some rural or low-traffic segments where alternative measures may be acceptable.

Criticality informs levels of service, response times, inspection frequency and investment priority.

## 3. Lifecycle Strategy by Asset Class

### 3.1 Street Lighting

#### 3.1.1 Planning and Design

- Use risk-based criteria to decide where lighting is warranted, considering road class, traffic volume, pedestrian activity, crash history and security needs.
- Apply recognised road-lighting design standards for luminance or illuminance, uniformity, glare and obtrusive light.
- Prefer luminaires with:
  - High energy efficiency.
  - Appropriate optical distribution.
  - Proven durability and available local support.

#### 3.1.2 Operation and Maintenance

- Combine:
  - **Reactive maintenance** for reported failures and safety-critical issues.
  - **Routine inspections or patrols** (including night-time observation or remote monitoring where CMS is available).
  - **Preventive maintenance** focusing on cleaning, tightening of terminals, inspection of brackets and foundations, and testing of protection devices.
- Establish response-time categories, for example:
  - Category A: safety-critical faults (e.g. lighting out at pedestrian crossings) – highest priority.
  - Category B: multiple lights out or feeder issues.
  - Category C: individual lamp outages on standard routes.

#### 3.1.3 Renewal and Upgrades

- Prioritise bulk renewal or retrofit of obsolete, inefficient or failure-prone luminaires and columns based on:
  - Condition and failure history.
  - Energy performance and tariff structure.
  - Safety and operational risk.
- Where feasible, integrate Control Management Systems (CMS) and dimming capabilities to support energy management and fault detection.

### 3.2 Traffic Signals

#### 3.2.1 Planning and Design

- Use traffic engineering analysis to determine where signals are warranted and what type of control is appropriate (fixed-time, actuated or adaptive).
- Ensure controller and detection technologies are selected for:
  - Safety and reliability.
  - Compatibility with existing systems.
  - Availability of spares and support.
- Document timing plans, phasing and safety parameters (intergreen times, clearance intervals, pedestrian timings).

#### 3.2.2 Operation and Maintenance

- Implement a structured preventive-maintenance regime covering:
  - Periodic cabinet and wiring inspections.
  - Conflict monitor testing and verification of safety interlocks.
  - Detector testing and tuning.
  - Cleaning and alignment of signal heads and lenses.
  - UPS inspection and battery tests.
- Use the CMMS to schedule and track all preventive and corrective work orders.
- Define priority categories and response times for:
  - All-dark or flashing faults.
  - Conflicting indications.
  - Detector failures and localised issues.

#### 3.2.3 Renewal and Upgrades

- Plan for periodic replacement or upgrade of controllers, detection technologies and signal heads based on:
  - Obsolescence and support status.
  - Failure history and performance.
  - New safety or operational requirements (for example public-transport priority).

## 4. Data and Information Strategy

- Define minimum data sets for each asset and ensure that operational systems capture:
  - Asset identity, location, type and key attributes.
  - Age, condition and failure history.
  - Work history and costs.
  - Energy use and tariffs where relevant.
- Maintain a GIS-based asset register interfaced with the CMMS for spatial analysis and planning.
- Apply data-quality rules and periodic data validation to support reliable decision-making.

## 5. Performance, Levels of Service and KPIs

This Strategy adopts the following performance concepts:

- **Availability** of:
  - Street lighting by corridor and area.
  - Traffic signals by intersection and route.
- **Response times** and **MTTR** for different fault categories.
- **Energy performance**, for example:
  - Energy consumption per lit point or per kilometre.
  - Trend in energy use over time after retrofit programmes.
- **Customer and safety indicators**, such as:
  - Complaints or reports per 1 000 assets.
  - Crash or incident statistics at key locations (used analytically rather than as sole indicators).

Targets derived from policy and stakeholder expectations shall be defined in the requirements specification and reviewed regularly.

## 6. Programme Development and Prioritisation

- Use risk-based and value-based prioritisation to develop:
  - Annual and multi-year maintenance and renewal programmes.
  - Specific retrofit and upgrade projects (for example LED conversions, controller replacements).
- Consider:
  - Asset criticality and exposure.
  - Condition and failure patterns.
  - Energy performance and potential savings.
  - Cost, available funding and delivery capacity.
- Document the rationale for major programme decisions to support traceability.

## 7. Interfaces to Other Systems and Processes

This Strategy interacts with:

- Governance processes in ERAGS-DOC-PROC-OV-001 (policy and strategy review, change control).
- Requirements and performance specifications in `/requirements`.
- Data models and analytics tools in `/models`, `/data` and `/qa`.
- Operational processes (planning, maintenance and projects) described in the `/processes` folder.

## 8. Review and Improvement

This Strategy shall be reviewed at least every three (3) years, or earlier when:

- There are significant changes in laws, regulations or standards affecting road lighting, traffic signals or electrical installations.
- New technologies or practices emerge that materially affect lifecycle cost or performance.
- Performance results highlight persistent gaps or opportunities for improvement.

Revisions shall follow the governance processes defined in ERAGS-DOC-PROC-OV-001, and updated versions shall maintain traceability to underlying data and analysis.
