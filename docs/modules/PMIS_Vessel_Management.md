# Vessel Management

## 1. Overview
The Vessel Management module governs the full lifecycle of vessel operations within the port environment, from identification and registration through port call planning, movement monitoring, and documentation oversight. It ensures vessel readiness, regulatory compliance, and operational coordination across port stakeholders.

## 2. Scope
### 2.1 In Scope
- Registration and master data management for all vessels calling the port.
- Port call planning and scheduling for arrivals, departures, movements, and berth preferences.
- Real-time tracking, status updates, and monitoring of vessel movements in port waters.
- Centralized management of vessel documentation, certificates, manifests, and compliance records.
- Business rules for validity, regulatory checks, and status-based workflows.

### 2.2 Out of Scope
- Berth design, configuration, and physical allocation calculations.
- Cargo loading/unloading operations and detailed cargo handling processes.
- Equipment scheduling, maintenance planning, and resource deployment.
- Billing, invoicing, and financial reconciliation.
- Labor assignment and crew management beyond vessel documentation needs.

## 3. Functional Requirements

### FR-V1: Vessel Registration
**Description**: Maintain a verified roster of vessels with all critical identification, classification, agent, and compliance details required for port entry and operations.

**Requirements**:
- Capture and store vessel IMO number, name, flag state, and call sign.
- Record vessel dimensions, including length overall (LOA), beam, draft, and tonnage.
- Classify vessels by type (container, bulk carrier, tanker, RoRo, general cargo) and class.
- Maintain up-to-date vessel agent and operator contact information.
- Track certification and compliance documentation linked to each vessel.
- Support upload and archival of vessel photos and supporting documentation.
- Preserve history of vessel information updates for audit and operational review.
- Record vessel service type and cargo handling capabilities where relevant.

**Business Rules**:
- BR-V1.1: A vessel record must not be accepted without a valid IMO number or equivalent registration identifier.
- BR-V1.2: Vessel dimensions must be recorded for planning and compatibility assessments.
- BR-V1.3: Vessel type classification must align with port operating policies and allowable cargo handling categories.
- BR-V1.4: Agent details must be current and available for any vessel that intends to call the port.
- BR-V1.5: Certification records must include expiry dates and status to support compliance checks.

**Workflow (WF-V1)**:
1. Receive vessel details from operator, agent, or existing master data source.
2. Validate registration fields and classify vessel type and service.
3. Attach agent contacts, compliance certificates, and supporting documents.
4. Confirm record completeness and register the vessel in the system.
5. Flag any missing or expired documentation for follow-up before port entry.

**Exception Handling**:
- If vessel IMO or registration identifier is missing → then reject registration and request required information.
- If vessel dimensions are incomplete or inconsistent → then mark record for verification before port call planning.
- If required agent or certificate details are missing → then restrict vessel from scheduling until data is complete.
- If vessel documentation expires before planned arrival → then require renewal or confirm exemption before acceptance.

**Priority**: Must Have

---

### FR-V2: Port Call Planning
**Description**: Organize and schedule vessel port calls with arrival and departure plans, berth preference inputs, special operational needs, and historical record support.

**Requirements**:
- Manage estimated time of arrival (ETA) and expected time of departure (ETD) for all port calls.
- Provide cargo manifest preview to support operational readiness and security checks.
- Notify vessel agents and port stakeholders of planning status and changes.
- Capture preferred berth or anchorage indication based on vessel type and special requirements.
- Identify and flag special conditions such as dangerous cargo, quarantine status, pilotage needs, or regulatory hold.
- Track multi-leg journeys with successive port calls and cumulative schedule context.
- Maintain historical port call records for performance, compliance, and dispute resolution.
- Allow planning updates for delays, cancellations, diversions, and emergency changes.

**Business Rules**:
- BR-V2.1: All port calls must have an ETA and ETD to support resource planning.
- BR-V2.2: Special requirements must be identified at planning time and visible to berth planning and safety teams.
- BR-V2.3: Changes to ETA/ETD require notification to vessel agent and impacted stakeholders.
- BR-V2.4: Cargo manifest visibility is mandatory for vessels arriving with declared cargo.
- BR-V2.5: Historical port call records must be retained for all completed and cancelled calls.

**Workflow (WF-V2)**:
1. Create the port call record for the vessel with ETA, ETD, and voyage details.
2. Record berth or anchorage preference and any special operational flags.
3. Review cargo manifest preview and ensure agent notification is prepared.
4. Monitor incoming updates and adjust plan for delays, diversions, or cancellations.
5. Finalize arrival plan and hand off to berth management and operations control.
6. Archive port call summary into historical records post-departure or cancellation.

**Exception Handling**:
- If ETA or ETD changes significantly → then issue updated notification and reassess berth/anchorage suitability.
- If the vessel reports emergency or sickness onboard → then prioritize crisis response and coordinate alternative berth or anchorage.
- If the port call is cancelled or diverted → then archive cancellation reason and notify all affected teams.
- If special requirements are later identified after planning → then escalate to operations and safety for immediate approval.

**Priority**: Must Have

---

### FR-V3: Vessel Tracking & Monitoring
**Description**: Monitor vessel movement and operational status within port waters to support safe navigation, arrival coordination, and congestion management.

**Requirements**:
- Integrate position updates from vessel movement monitoring sources.
- Display current vessel position relative to the port and anchorage areas.
- Capture speed and heading information for situational awareness.
- Log port entry and exit events for all vessels.
- Monitor vessel status categories such as arriving, berthed, departing, or anchored.
- Provide alerts for port congestion and vessel queueing issues.
- Monitor deviations from planned schedules and trigger review when thresholds are exceeded.
- Support status changes for emergency stops, drifting, or failed transit.

**Business Rules**:
- BR-V3.1: All vessels in port waters must have an operational tracking record while under port control.
- BR-V3.2: Entry and exit events are required for operational and regulatory audit.
- BR-V3.3: Vessel status updates must be synchronized with port call planning and berth occupancy data.
- BR-V3.4: Congestion alerts should be generated when arrivals exceed available capacity or safe passing limits.
- BR-V3.5: Deviations from planned ETA/ETD beyond defined thresholds must be escalated to port operations.

**Workflow (WF-V3)**:
1. Record the vessel’s inbound movement and planned approach.
2. Track position, speed, and heading through the arrival phase.
3. Update status as the vessel enters the port, anchors, or proceeds to berth.
4. Monitor the berth occupancy and coordinate onward movement or departure.
5. Log exit from port waters and complete the movement record.
6. Review deviations and update historical performance metrics.

**Exception Handling**:
- If vessel deviates from planned route or schedule → then alert operations and assess impact on berth allocation.
- If port congestion is detected → then trigger congestion mitigation and reschedule affected vessels.
- If vessel stops unexpectedly or presents a hazard → then notify safety and maritime authorities immediately.
- If status does not update for an extended period → then verify communications and confirm actual vessel condition.

**Priority**: Must Have

---

### FR-V4: Vessel Documentation Management
**Description**: Centralize vessel-related documentation to ensure compliance with port, national, and international regulations, and to support operational decision-making.

**Requirements**:
- Store safety, class society, and environmental certificates for each vessel.
- Maintain crew manifest documentation linked to port call requirements.
- Capture insurance documentation and vessel indemnity records.
- Record port state control reports and related inspection findings.
- Archive surveyor reports and inspection outcomes.
- Track document expiry dates and issue proactive alerts ahead of expiry.
- Support digital signature verification and document authentication as a business-level requirement.
- Link documentation status with vessel operability and port call clearance.

**Business Rules**:
- BR-V4.1: Vessel clearance for port entry requires valid and unexpired mandatory certificates.
- BR-V4.2: Crew manifests must be available for vessels arriving with personnel changes, quarantine risk, or regulatory inspection.
- BR-V4.3: Insurance documentation must meet port authority requirements before arrival approval.
- BR-V4.4: Port state control and surveyor reports must be retained for the duration required by regulation.
- BR-V4.5: Expiry alerts must be raised sufficiently in advance to avoid last-minute clearance issues.

**Workflow (WF-V4)**:
1. Collect required vessel certificates and supporting documentation from the vessel agent.
2. Verify document type, validity period, and relevance to the upcoming port call.
3. Log documents in the vessel’s profile and link them to active port calls.
4. Monitor expiry dates and notify stakeholders when renewal is required.
5. Use documentation status to condition port call approval and operational readiness.
6. Archive completed documentation records after passage and retain them according to compliance rules.

**Exception Handling**:
- If a required certificate is expired or missing → then withhold port call approval and request immediate renewal.
- If the crew manifest is incomplete or inconsistent → then require clarification before vessel arrival.
- If a port state control report indicates non-compliance → then escalate to regulatory and operations teams.
- If insurance documentation does not meet requirements → then deny access until acceptable coverage is confirmed.

**Priority**: Must Have

## 4. Global Business Rules
- G-BR1: Vessel registration, port call planning, tracking, and documentation must be coordinated to support a single authoritative vessel profile.
- G-BR2: All vessel-related data must be auditable, with update history preserved for compliance and dispute resolution.
- G-BR3: Vessel acceptance into the port is conditional on valid registration, operational planning, tracking visibility, and compliant documentation.
- G-BR4: Alerts and exceptions must be communicated to vessel agents and internal port stakeholders in a timely manner.
- G-BR5: Historical port call and movement records must be retained for operational review and regulatory reporting.

## 5. Assumptions
- Vessel agents provide accurate and timely information for registration and port call planning.
- Port authorities require documented evidence of compliance before vessel clearance.
- Port operations rely on up-to-date vessel status and schedule information to coordinate resources.
- Special cargo, quarantine, and emergency conditions are declared in advance when possible.
- Historical records are used to improve future planning and manage operational exceptions.

## 6. Constraints
- Vessel call planning must operate within port capacity, berth availability, and safety restrictions.
- Documentation management is constrained by regulatory renewal cycles and inspection timelines.
- Tracking and monitoring depend on vessels operating within port-designated areas and reporting status updates.
- Emergency and delay scenarios may require rapid re-prioritization of vessel movements and port resources.
- Vessel classification and dimension data must match port operating limitations for draft, length, and cargo type.

## 7. Success Metrics
- Percentage of vessel records completed with valid registration and documentation before port call approval.
- Accuracy of ETA/ETD planning and reduction in schedule deviations.
- Number of vessel movements tracked without status gaps or delays in port waters.
- Rate of expired or missing documentation detected before vessel arrival.
- Reduction in emergency berth reassignments and unscheduled diversions due to proactive planning.
- Timeliness of alerts for special requirements, regulatory holds, and vessel compliance issues.
