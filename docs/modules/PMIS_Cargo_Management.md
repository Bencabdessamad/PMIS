# Cargo Management

## 1. Overview
The Cargo Management module governs planning, tracking, container handling, dangerous goods control, and import/export processing for port cargo operations. It supports cargo visibility, regulatory compliance, and operational coordination across terminal and customs workflows.

## 2. Scope
### 2.1 In Scope
- Planning cargo handling operations from arrival through storage to release.
- Tracking cargo movements and condition monitoring in real time.
- Managing container inventory, status, and related handling actions.
- Handling dangerous goods compliance, segregation, and incident management.
- Supporting import and export processing with customs documentation and release workflows.

### 2.2 Out of Scope
- Vessel registration and berth allocation.
- Equipment scheduling beyond cargo handling requirements.
- Financial billing, invoicing, and payment reconciliation.
- Labor assignment outside cargo handling execution.

## 3. Functional Requirements

### FR-C1: Cargo Operations Planning
**Description**: Plan and coordinate cargo handling operations across vessel, yard, and warehouse activities with emphasis on safety, throughput, and regulatory requirements.

**Requirements**:
- Import bill of lading (B/L) or cargo declaration data for planning.
- Classify cargo by type, weight, volume, and handling requirements.
- Identify hazardous cargo and ensure regulation compliance.
- Assign storage location based on cargo characteristics and operational priorities.
- Determine required handling equipment and lift sequences.
- Generate operations timelines for loading, unloading, and transfer.
- Create and maintain stowage plans for vessel, yard, and storage areas.
- Account for shift changes, resource availability, and customs clearance timing.
- Include contingency planning for delays, damaged cargo, and customs holds.

**Business Rules**:
- BR-C1.1: Cargo planning must use the latest manifest and declaration information.
- BR-C1.2: Hazardous cargo must be classified and handled in accordance with IMDG, SOLAS, and MARPOL business requirements.
- BR-C1.3: Storage assignment must reflect cargo compatibility, temperature control needs, and segregation rules.
- BR-C1.4: Equipment requirements must be validated prior to operation execution.
- BR-C1.5: Cargo handling plans must include contingencies for damage, wrong delivery, or customs inspection delays.

**Workflow (WF-C1)**:
1. Receive cargo documentation and manifest data from vessel agent or operator.
2. Confirm cargo classification, weight, volume, and handling requirements.
3. Assign storage or yard location and required handling equipment.
4. Create operations timeline and stowage plan, considering customs clearance and vessel schedule.
5. Review plan for hazardous cargo restrictions and regulatory compliance.
6. Publish the plan to terminal operations and monitor for changes.

**Exception Handling**:
- If cargo documentation is incomplete or missing → then hold planning and request required information.
- If a cargo item is re-classified as hazardous after planning → then update handling plan and notify safety teams.
- If storage capacity is unavailable for the assigned cargo type → then reassign location or delay receipt.
- If vessel or cargo arrival is delayed → then revise timeline and coordinate resource adjustments.

**Priority**: Must Have

---

### FR-C2: Cargo Tracking & Monitoring
**Description**: Track cargo movement and condition from arrival through storage and onward release to maintain visibility, minimize loss, and ensure compliance.

**Requirements**:
- Track cargo location through warehouse, yard, vessel, and gate movements.
- Log cargo movement history and chain of custody details.
- Capture temperature and humidity monitoring for perishables.
- Calculate cargo dwell time for stored consignments.
- Monitor cargo condition indicators and report damage or theft risks.
- Capture photographic evidence for damage or condition inspections.
- Integrate with RFID or barcode systems where available.
- Record exceptions such as misdirected cargo, missing documents, and customs holds.
- Provide status updates to stakeholders during cargo lifecycle.

**Business Rules**:
- BR-C2.1: Cargo must be tracked from receipt to release, with all location changes logged.
- BR-C2.2: Perishable cargo condition monitoring must meet required temperature/humidity thresholds.
- BR-C2.3: Chain of custody records are mandatory for high-value or sensitive cargo.
- BR-C2.4: Damage, theft, or condition exceptions must be recorded and escalated promptly.
- BR-C2.5: Missing documentation or customs holds must prevent release until resolved.

**Workflow (WF-C2)**:
1. Register cargo upon receipt and assign a tracking identifier.
2. Update location and status with each movement or handling event.
3. Monitor environmental condition data for temperature-sensitive goods.
4. Log chain of custody and supporting evidence for control and audits.
5. Alert operations when cargo is damaged, missing, or held for inspection.
6. Confirm release only after all tracking, condition, and documentation conditions are satisfied.

**Exception Handling**:
- If cargo is damaged during handling → then document the damage, notify claims and safety teams, and quarantine if required.
- If cargo is misdirected or moved to the wrong location → then trace the movement, correct the location, and review process gaps.
- If temperature/humidity thresholds are exceeded → then trigger preservation action and inspect the cargo condition.
- If cargo is held by customs → then log the hold reason and do not release until clearance is received.

**Priority**: Must Have

---

### FR-C3: Container Management
**Description**: Manage container inventory, identification, condition, and movement across port operations to support efficient handling and minimize detention costs.

**Requirements**:
- Record container identification, type, and size (20ft, 40ft, HC, etc.).
- Track container status such as empty, loaded, damaged, or under repair.
- Support damage reporting and repair tracking for containers.
- Maintain container movement history across gate-in, yard, vessel, and gate-out events.
- Capture container gate-in/gate-out records and related custody details.
- Calculate detention and demurrage exposure for containers in the terminal.
- Manage container availability for loading or dispatch.
- Record container condition inspections and repair requirements.
- Link container events to cargo plans and vessel operations.

**Business Rules**:
- BR-C3.1: Container identification must be maintained consistently through the cargo lifecycle.
- BR-C3.2: Damaged or unfit containers must be quarantined until inspected and repaired.
- BR-C3.3: Gate-in and gate-out events are required for all containers entering or leaving the terminal.
- BR-C3.4: Detention and demurrage must be monitored and managed to reduce penalties.
- BR-C3.5: Container condition and availability must be visible before assignment to loading or discharge operations.

**Workflow (WF-C3)**:
1. Register container details at gate-in or upon receipt.
2. Verify container condition and record any damage.
3. Update status as the container moves through yard, loading, or discharge operations.
4. Track gate-out and release events for container departure.
5. Record repair work and availability changes for damaged containers.
6. Monitor detention and demurrage exposure and take corrective action.

**Exception Handling**:
- If a container is found damaged at gate-in → then quarantine it and document required repairs before use.
- If a container’s identification is unreadable or inconsistent → then verify against physical records and correct the entry.
- If a container remains beyond allowable detention → then escalate to commercial and terminal operations.
- If a container is incorrectly marked empty/loaded → then reconcile status with cargo records before movement.

**Priority**: Must Have

---

### FR-C4: Dangerous Goods Management
**Description**: Control the handling, storage, and movement of dangerous goods to comply with maritime safety regulations and minimize environmental and safety risks.

**Requirements**:
- Classify and document dangerous goods according to IMDG, SOLAS, and MARPOL requirements.
- Enforce segregation rules and storage location restrictions.
- Maintain safety documentation including MSDS and shipper’s declarations.
- Record incident reports for accidents or dangerous goods deviations.
- Monitor environmental compliance and safe handling procedures.
- Verify insurance and liability coverage for dangerous goods shipments.
- Track special handling instructions and regulatory hold conditions.
- Log emergency response and incident escalation for dangerous goods events.

**Business Rules**:
- BR-C4.1: Dangerous goods must be classified and handled according to IMDG code requirements.
- BR-C4.2: Segregation and storage restrictions must be enforced for incompatible cargoes.
- BR-C4.3: Safety documentation must be available before dangerous goods are moved or stored.
- BR-C4.4: Incidents involving dangerous goods require immediate escalation and record-keeping.
- BR-C4.5: Environmental and port authority rules must be honored during dangerous goods operations.

**Workflow (WF-C4)**:
1. Receive dangerous goods declarations and verify classification.
2. Confirm storage and handling restrictions with terminal safety officers.
3. Assign secure and compliant storage or handling areas.
4. Track movement and document all handling activities.
5. Report any incidents or deviations to safety and regulatory authorities.
6. Close out the shipment after safe completion and retain incident documentation.

**Exception Handling**:
- If dangerous goods documentation is missing or incomplete → then refuse movement and hold cargo until properly documented.
- If segregation rules cannot be met in the planned storage area → then identify an alternate compliant location.
- If a dangerous goods incident occurs → then initiate emergency response and quarantine affected cargo.
- If regulatory inspections require additional controls → then update handling requirements and notify operations.

**Priority**: Must Have

---

### FR-C5: Import/Export Processing
**Description**: Manage import and export cargo processing workflows from customs documentation through release, ensuring compliance with authorities and efficient cargo movement.

**Requirements**:
- Submit customs documentation and related declarations for import/export cargo.
- Support port authority clearance workflows and release order generation.
- Coordinate final delivery and receipt acknowledgement.
- Manage discrepancies and exception handling for cargo documentation.
- Support electronic data interchange (EDI) with customs and supply chain partners.
- Integrate with customs authorities for release and hold decisions.
- Track clearance status and coordinates handover to consignee or onward transport.
- Record customs holds, inspections, and required corrective actions.

**Business Rules**:
- BR-C5.1: Cargo must not be released without proper customs clearance and release documentation.
- BR-C5.2: Discrepancies in documentation must be resolved before delivery or load-out.
- BR-C5.3: Electronic messaging with customs authorities is required for timely clearance.
- BR-C5.4: Release orders must be matched to cargo and consignee details.
- BR-C5.5: Customs holds must be logged and prevent cargo movement until released.

**Workflow (WF-C5)**:
1. Capture import/export documentation and verify cargo details.
2. Submit required documentation to customs and port authority systems.
3. Monitor clearance status and respond to inspection or hold requests.
4. Generate release orders once clearance is granted.
5. Coordinate delivery or onward transport with consignee and terminal operations.
6. Record completion and retain documentation for audit.

**Exception Handling**:
- If customs documentation is incomplete or inconsistent → then withhold cargo release and request correction.
- If cargo is placed on customs hold → then log the hold and do not move the cargo until cleared.
- If delivery instructions are incorrect or missing → then verify consignee details before shipment.
- If export cargo is refused or reclassified by customs → then return cargo to holding location and manage re-export or disposal.

**Priority**: Must Have

## 4. Global Business Rules
- G-BR1: Cargo operations must be driven by accurate manifest, declaration, and regulatory data.
- G-BR2: Cargo visibility and condition tracking are mandatory throughout the terminal lifecycle.
- G-BR3: All hazardous and dangerous goods must comply with applicable maritime and port regulations.
- G-BR4: Cargo release is conditional on customs clearance, documentation completeness, and operational readiness.
- G-BR5: Exceptions and incidents must be captured, escalated, and retained for audit and continuous improvement.

## 5. Assumptions
- Cargo information from carriers and agents is timely and sufficiently detailed.
- Customs and regulatory authorities provide clearance decisions within expected operational windows.
- Port handling equipment and storage capacity are available to meet planned cargo needs.
- Terminal operations can respond to damage, holds, and other exceptions as they arise.
- Historical cargo data supports future planning and performance improvement.

## 6. Constraints
- Cargo handling is constrained by storage capacity, equipment availability, and operational windows.
- Regulatory holds, customs inspections, and dangerous goods controls can delay cargo movement.
- Perishable cargo depends on reliable temperature-controlled storage and monitoring.
- Import/export processing is constrained by customs office hours, document accuracy, and authority response times.
- Container availability and terminal gate capacity limit cargo throughput.

## 7. Success Metrics
- Percentage of cargo handled per plan without documentation or customs exceptions.
- Reduction in cargo dwell time and increase in throughput.
- Number of damage or condition incidents recorded and resolved.
- Accuracy of container status records and reduction in detention/demurrage exposures.
- Percentage of dangerous goods shipments handled in full regulatory compliance.
- Timeliness of import/export clearance and reduction in customs holds.
