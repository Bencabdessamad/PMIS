# Equipment Management

## 1. Overview
The Equipment Management module governs port equipment lifecycle, allocation, and maintenance to ensure terminal operations remain productive, safe, and compliant with regulatory and operational standards.

## 2. Scope
### 2.1 In Scope
- Inventory management of port equipment including cranes, forklifts, conveyors, and other handling assets.
- Scheduling equipment assignments for cargo handling, vessel operations, and support tasks.
- Maintenance planning, tracking, and repair coordination for preventive and corrective activities.
- Monitoring equipment status, availability, and compliance with safety certifications.

### 2.2 Out of Scope
- Detailed cargo planning or berth assignments beyond equipment requirements.
- Financial invoicing and billing for equipment usage.
- Crew and labor management beyond operator assignment to equipment.
- Vessel or berth documentation management unrelated to equipment operations.

## 3. Functional Requirements

### FR-E1: Equipment Inventory
**Description**: Maintain a comprehensive inventory of equipment assets, including specifications, condition, and operational readiness.

**Requirements**:
- Register equipment details such as type, model, capacity, and unique identification.
- Document operational specifications and capabilities for each equipment item.
- Track equipment status categories including available, in-use, maintenance, and out-of-service.
- Record maintenance history and safety inspection findings for each asset.
- Capture equipment location within the port and assignment history.
- Monitor certification status and verify safety compliance requirements.
- Associate equipment attachments and accessories with the primary asset.
- Track depreciation or lifecycle stage for planning replacement and upgrades.

**Business Rules**:
- BR-E1.1: Equipment must have a unique identifier and documented specifications prior to assignment.
- BR-E1.2: Safety certifications must be current for equipment to be considered operational.
- BR-E1.3: Equipment status must reflect actual readiness and prevent assignment when unfit.
- BR-E1.4: Maintenance history must be retained to support operational decisions and audits.
- BR-E1.5: Equipment location and assignment history must be updated with each movement.

**Workflow (WF-E1)**:
1. Register new equipment with specifications, capacity, and classification.
2. Record certification and safety inspection status.
3. Update equipment location and operational status as assets move or change condition.
4. Log maintenance and inspection events in the equipment history.
5. Review equipment readiness before it is scheduled for operations.

**Exception Handling**:
- If equipment lacks a valid safety certification → then mark it unavailable and schedule an inspection.
- If equipment status is inconsistent with physical condition → then verify the asset and correct the record.
- If location data is missing or outdated → then reconcile with physical inventory and update the asset record.
- If maintenance history is incomplete → then require validation before the equipment can be returned to service.

**Priority**: Must Have

---

### FR-E2: Equipment Scheduling
**Description**: Assign and coordinate equipment usage for port operations while managing conflicts, capacity, and operator availability.

**Requirements**:
- Provide equipment availability calendars to support operational planning.
- Assign equipment to operations with start/end times and location details.
- Detect scheduling conflicts and prevent double booking.
- Manage overtime and extended use when operations exceed planned duration.
- Support equipment relocation planning between yard, berth, and storage areas.
- Assign operators to equipment where required and record skill or certification needs.
- Monitor equipment utilization and adjust assignments for changing priorities.
- Support reassignment in case of breakdowns, operator absence, or emergency operational changes.

**Business Rules**:
- BR-E2.1: Equipment must be scheduled only when it is available, certified, and in operational condition.
- BR-E2.2: Scheduling conflicts must be resolved before assignment confirmation.
- BR-E2.3: Operator qualification or certification requirements must be satisfied for assigned equipment.
- BR-E2.4: Overtime usage must be captured and approved according to port operational policy.
- BR-E2.5: Emergency reassignments take precedence over routine planning when safety or cargo operations demand it.

**Workflow (WF-E2)**:
1. Review equipment availability and operational requirements for the planned activity.
2. Select suitable equipment and verify certification, location, and readiness.
3. Assign equipment to the operation with defined start/end times and required resources.
4. Monitor the assignment for delays, breakdowns, or operator issues.
5. Reassign equipment or escalate if the scheduled asset becomes unavailable.
6. Close out the assignment and capture actual usage details for reporting.

**Exception Handling**:
- If scheduled equipment breaks down before or during use → then activate a fallback assignment and notify operational planners.
- If the assigned operator is unavailable → then reassign a qualified operator or reschedule the equipment.
- If equipment usage extends beyond the scheduled window → then document overtime and review resource impact.
- If an overload or operational conflict arises → then suspend the assignment and escalate to management.

**Priority**: Must Have

---

### FR-E3: Equipment Maintenance
**Description**: Plan, execute, and track preventive and corrective maintenance to maintain equipment safety, reliability, and operational availability.

**Requirements**:
- Create maintenance schedules for preventive inspections and routine servicing.
- Generate and track work orders for corrective repairs and emergency interventions.
- Manage spare parts and support materials required for maintenance tasks.
- Record maintenance costs, downtime, and repair outcomes.
- Log equipment performance metrics and identify recurring issues.
- Track maintenance history for regulatory inspections and asset lifecycle planning.
- Coordinate maintenance activities to minimize impact on planned operations.
- Support unplanned maintenance and emergency repairs during breakdowns.

**Business Rules**:
- BR-E3.1: Equipment scheduled for maintenance must be unavailable for operational assignment.
- BR-E3.2: Emergency repairs must be prioritized when equipment failure threatens safety or critical operations.
- BR-E3.3: Maintenance history must be retained to support inspection and compliance requirements.
- BR-E3.4: Spare parts availability influences maintenance scheduling and equipment return-to-service timing.
- BR-E3.5: Maintenance work orders must include estimated return-to-service and be updated when repair status changes.

**Workflow (WF-E3)**:
1. Plan preventive maintenance based on usage, manufacturer guidance, or inspection schedules.
2. Create work orders and allocate required personnel, parts, and time.
3. Remove equipment from operational schedules for the maintenance window.
4. Execute maintenance or repair activities and record details of the work performed.
5. Validate repair outcomes and return the equipment to service when certified.
6. Update maintenance history and analyze performance trends.

**Exception Handling**:
- If a maintenance task uncovers a major defect → then extend the repair window and notify affected operations.
- If spare parts are unavailable → then reschedule maintenance and communicate the revised return-to-service date.
- If emergency breakdown occurs during operations → then initiate immediate repair actions and arrange substitute equipment.
- If maintenance completion falls behind schedule → then update availability forecasts and revise equipment assignments.

**Priority**: Must Have

## 4. Global Business Rules
- G-BR1: Equipment must be managed consistently across inventory, scheduling, and maintenance records.
- G-BR2: Operational readiness requires valid certifications, current status, and confirmed availability.
- G-BR3: Maintenance planning must balance asset reliability with operational demand and safety requirements.
- G-BR4: Equipment assignments and changes must be documented to support accountability and audit readiness.
- G-BR5: Emergency repair and reallocation processes must be in place to minimize disruption.

## 5. Assumptions
- Equipment data is maintained by operations with up-to-date specifications and certification status.
- Equipment availability information is available in time to support operational planning.
- Maintenance resources and spare parts are managed to support planned and unplanned repairs.
- Equipment operators are qualified and available according to assignment requirements.
- Asset performance history is used to improve maintenance and scheduling decisions.

## 6. Constraints
- Equipment management is constrained by the number of available assets and qualified operators.
- Planned and unplanned maintenance reduces available equipment capacity.
- Safety certifications and inspection requirements limit equipment deployment.
- Breakdowns and emergency repairs can disrupt planned schedules and increase operational risk.
- Equipment relocation and staging require time and coordination with terminal operations.

## 7. Success Metrics
- Percentage of equipment assignments completed on schedule without breakdowns.
- Reduction in unscheduled maintenance incidents and equipment downtime.
- Percentage of equipment with current safety certification and inspection status.
- Time to reassign equipment after a breakdown or operator absence.
- Accuracy of equipment availability forecasts against actual usage.
- Reduction in maintenance backlog and improved return-to-service timelines.
