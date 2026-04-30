# Berth Management

## 1. Overview
The Berth Management module defines, allocates, monitors, and maintains port berth resources. It supports operational planning and execution by ensuring berths are properly configured, assigned, occupied, and maintained while managing conflicts, vessel delays, and emergency berthing scenarios.

## 2. Scope
### 2.1 In Scope
- Definition and management of berth properties, capabilities, and special facility availability.
- Assignment of vessels to berths with consideration of vessel dimensions, cargo, draft restrictions, and operational priorities.
- Monitoring berth occupancy, utilization, idle time, and congestion.
- Management of berth maintenance schedules, closures, unavailability notifications, and impact on vessel scheduling.

### 2.2 Out of Scope
- Cargo handling operational execution, equipment movement, and load/unload sequencing.
- Detailed vessel registration, port call planning, or documentation management.
- Financial billing, tariff calculation, and invoicing.
- Labor planning and workforce assignment beyond berth readiness.

## 3. Functional Requirements

### FR-B1: Berth Configuration
**Description**: Define and manage physical berth attributes, handling capabilities, and special service availability to ensure each berth is fit for purpose and compliant with port operating rules.

**Requirements**:
- Record berth identification, name, and location within the port.
- Document berth dimensions including length, depth, and width.
- Maintain equipment availability at each berth such as cranes, forklifts, conveyors, and shore services.
- Define handling capacity specifications for cargo tonnage, container types, and vessel classes.
- Capture draft restrictions and maximum permissible vessel dimensions.
- Specify vessel type compatibility rules and berth suitability for tankers, containers, RoRo, bulk carriers, and general cargo vessels.
- Track availability of special facilities such as shore power supply, fresh water, bunkering, waste reception, and hazardous cargo handling.
- Maintain maintenance schedules and planned outage windows for berth readiness.
- Include regulatory and safety restrictions such as SOLAS separation distances, environmental zone rules, and port authority berth classifications.

**Business Rules**:
- BR-B1.1: Each berth must have a unique identifier and clearly documented dimensions before it can be used for allocation.
- BR-B1.2: Berth suitability must be determined by vessel type, draft, and special facility requirements.
- BR-B1.3: Draft restrictions and special facilities must be applied to allocation decisions and operational readiness checks.
- BR-B1.4: Berth maintenance windows must be published and enforced to prevent planned allocation during unavailable periods.
- BR-B1.5: Safety and regulatory requirements must be associated with specific berths and observed during berth configuration.

**Workflow (WF-B1)**:
1. Define or review the berth inventory and assign identifiers and characteristics.
2. Capture dimensions, capacity, and available equipment for each berth.
3. Record special facility support and regulatory restrictions for each berth.
4. Schedule planned maintenance and annotate periods of berth unavailability.
5. Validate berth configuration against port safety rules and readiness criteria.

**Exception Handling**:
- If berth dimensions or draft restrictions are incomplete → then mark the berth as unavailable until details are confirmed.
- If special facility availability changes unexpectedly → then update configuration and notify allocation planners.
- If a berth is designated for restricted cargo but lacks required facilities → then prohibit allocations for that cargo type.
- If maintenance schedule overlaps with planned vessel allocation → then revise allocation or reschedule maintenance.

**Priority**: Must Have

---

### FR-B2: Berth Allocation
**Description**: Assign vessels to berths using operational priorities, vessel compatibility, turnaround objectives, and conflict resolution, while accommodating manual planner adjustments.

**Requirements**:
- Evaluate berth assignment based on vessel dimensions, draft, and compatibility with berth rules.
- Consider cargo type compatibility, hazardous cargo restrictions, and berth facilities.
- Optimize berth selection to support turnaround time efficiency and minimize idle time.
- Manage priority queues for vessels such as passenger ships, hazardous cargo, and high-priority imports/exports.
- Allow manual override for planners to adjust berth assignments in exceptional situations.
- Detect and prevent berth collisions by identifying overlapping allocation windows.
- Display real-time berth availability and booking status.
- Support multi-criteria optimization including cost, time, equipment readiness, and operational constraints.
- Retain historical allocation performance metrics for review and continuous improvement.
- Enforce SOLAS separation and port authority berth assignment policies where applicable.

**Business Rules**:
- BR-B2.1: Berth allocation must only assign vessels to berths capable of handling the vessel’s size, draft, and cargo type.
- BR-B2.2: Priority vessels and emergency berths receive precedence over standard allocations when operational conditions require.
- BR-B2.3: Manual overrides are permitted but must be documented with rationale and impact assessment.
- BR-B2.4: Berth collision windows are not allowed; overlapping vessel allocations must be resolved before confirmation.
- BR-B2.5: Allocation decisions must factor maintenance schedules and known berth unavailability.

**Workflow (WF-B2)**:
1. Receive vessel and port call details including dimensions, cargo needs, and arrival schedule.
2. Identify candidate berths based on configuration, draft, and facility compatibility.
3. Evaluate allocation against turnaround, priority, and operational constraints.
4. Confirm berth assignment and communicate the selection to vessel operations and port control.
5. Monitor for delays or conflicts and revise the allocation if required.
6. Archive allocation outcomes and performance metrics for future planning.

**Exception Handling**:
- If no suitable berth is available for the vessel’s size or cargo type → then escalate to operations to identify alternatives or delay acceptance.
- If a vessel is delayed and its berth assignment conflicts with another scheduled arrival → then reallocate berths and notify affected stakeholders.
- If an emergency berthing request occurs → then reserve or reassign a berth and reprioritize existing allocations.
- If a berth becomes unexpectedly unavailable → then trigger contingency allocation and communicate revised plans.

**Priority**: Must Have

---

### FR-B3: Berth Occupancy Management
**Description**: Monitor actual berth use and utilization to support operational efficiency, identify congestion, and optimize berth deployment.

**Requirements**:
- Display real-time berth occupancy status for all active berths.
- Track occupancy duration for vessels berthed, loading, or discharging.
- Monitor idle time between vessel operations and berth usage gaps.
- Calculate berth utilization rates and identify underused capacity.
- Detect congestion conditions based on berth queueing, vessel hold times, and port movement constraints.
- Forecast berth occupancy and peak demand periods using scheduled and actual vessel activity.
- Identify peak hour pressure points and opportunities for operational smoothing.
- Maintain occupancy data to support turnaround analysis and berth performance reporting.
- Apply safety limits to occupancy when vessels carry hazardous or restricted cargo.

**Business Rules**:
- BR-B3.1: Berth occupancy status must be updated whenever a vessel arrives, departs, or changes operational status.
- BR-B3.2: Idle time beyond acceptable thresholds should be flagged for operational review.
- BR-B3.3: Congestion conditions must trigger review and mitigation actions when berth queue length or delay exceeds thresholds.
- BR-B3.4: Occupancy forecasting must consider both planned arrivals and actual delay impacts.
- BR-B3.5: Peak hour identification should influence future allocation strategies and staffing plans.

**Workflow (WF-B3)**:
1. Capture berth occupation events from vessel arrival and departure records.
2. Update berth status in real time as vessels occupy, vacate, or remain idle.
3. Measure occupancy duration and calculate utilization metrics.
4. Identify congestion and peak periods through analysis of scheduled versus actual movements.
5. Recommend operational adjustments based on occupancy insights.
6. Report berth utilization and improvement opportunities to port management.

**Exception Handling**:
- If a berth remains occupied beyond the expected departure time → then notify planners and reassess downstream berth assignments.
- If vessel operations are extended due to cargo handling delays → then revise occupancy forecasts and adjust subsequent allocations.
- If congestion is detected at peak periods → then evaluate re-sequencing, use of alternate berths, or temporary vessel hold arrangements.
- If berth occupancy metrics indicate excessive idle time → then investigate causes and address operational inefficiencies.

**Priority**: Must Have

---

### FR-B4: Berth Maintenance & Operations
**Description**: Manage berth maintenance planning, availability notifications, and operational readiness to minimize disruption to vessel scheduling.

**Requirements**:
- Create and track berth maintenance schedules for inspections, repairs, and upgrades.
- Manage work orders and associated operational impacts for berth maintenance activities.
- Log maintenance history and record past unavailability events.
- Notify stakeholders of berth unavailability due to maintenance, inspections, or operational closures.
- Capture estimated return to service dates for berths undergoing maintenance.
- Assess maintenance impacts on vessel scheduling and berth allocation plans.
- Include emergency maintenance closures and temporary restrictions in operational planning.
- Ensure maintenance planning respects regulatory safety requirements and port authority approvals.

**Business Rules**:
- BR-B4.1: Berths under maintenance must be marked unavailable for allocation during the entire maintenance window.
- BR-B4.2: Maintenance work orders must be coordinated with vessel schedules to avoid unnecessary disruptions.
- BR-B4.3: Estimated return to service dates must be updated when maintenance progress changes.
- BR-B4.4: Emergency maintenance closures require immediate notification and alternative berth planning.
- BR-B4.5: Maintenance history should be retained to support planning and reliability improvement.

**Workflow (WF-B4)**:
1. Plan berth maintenance activities and define the duration and scope.
2. Issue work orders and schedule maintenance against berth availability.
3. Mark berths unavailable during maintenance and notify allocation teams.
4. Monitor progress and update return to service dates as required.
5. Assess the effect of maintenance on upcoming vessel allocations and revise schedules.
6. Record completed maintenance and analyze outcomes for future planning.

**Exception Handling**:
- If maintenance runs longer than planned → then extend berth unavailability, reschedule affected vessels, and communicate the delay.
- If a berth becomes unsafe or requires emergency closure → then immediately restrict allocations and identify alternative berths.
- If maintenance completion is earlier than expected → then restore berth availability and notify operational planners.
- If conflicting maintenance and vessel allocations are discovered → then resolve the conflict with priority given to safety and regulatory compliance.

**Priority**: Must Have

## 4. Global Business Rules
- G-BR1: Berth planning and operations must always reflect the latest berth configuration, maintenance status, and vessel requirements.
- G-BR2: Berth assignments must comply with safety regulations, port authority rules, and vessel-specific restrictions.
- G-BR3: All berth activity must be auditable and retain history for incident review, regulatory reporting, and performance analysis.
- G-BR4: Emergency and delay conditions must be handled with documented escalation and communication to stakeholders.
- G-BR5: Berth utilization and maintenance planning should support continuous improvement and operational resilience.

## 5. Assumptions
- Berth configuration data is maintained by port operations with accurate dimensions and facility details.
- Vessel arrival and cargo information are available in time to support berth allocation decisions.
- Maintenance schedules are planned and coordinated with port scheduling teams.
- Regulatory and safety restrictions are clearly defined for berth assignments.
- Port operations can adjust berth allocations dynamically in response to delays and emergencies.

## 6. Constraints
- Berth capacity is constrained by physical dimensions, draft limitations, and equipment availability.
- Operational allocation must respect maintenance windows and berth unavailability periods.
- Safety separations and regulatory berth restrictions limit berth flexibility.
- Vessel delays and emergency berthing can force reallocation and impact service performance.
- Congestion at peak periods constrains berth utilization and may require queuing or alternative arrangements.

## 7. Success Metrics
- Percentage of berth allocations completed without conflict or reallocation.
- Average berth utilization rate and reduction in idle berth time.
- Number of berth conflicts or collisions avoided through effective planning.
- Timeliness of berth availability updates for maintenance and unplanned closures.
- Reduction in berth allocation changes due to delays, emergencies, or scheduling errors.
- Accuracy of occupancy forecasts and peak period demand planning.
