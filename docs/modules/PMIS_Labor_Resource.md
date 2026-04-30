# Labor & Resource Management

## 1. Overview
The Labor & Resource Management module coordinates personnel planning, shift management, and security staff deployment within port operations. It ensures the right skills and certifications are available at the right time while addressing regulatory labor requirements and emergent operational needs.

## 2. Scope
### 2.1 In Scope
- Management of employee and contractor profiles, certifications, and skill assignments.
- Creation and adjustment of work schedules for shift-based port operations.
- Assignment and coordination of security personnel and patrol duties.
- Tracking availability, performance, training, and compliance with labor regulations.

### 2.2 Out of Scope
- Detailed payroll processing or compensation calculation.
- Financial management of labor cost allocation beyond scheduling visibility.
- Vessel, berth, cargo, or equipment operational planning outside of staffing needs.
- External communication systems beyond internal labor and security coordination.

## 3. Functional Requirements

### FR-L1: Personnel Management
**Description**: Manage port employees and contractors, their qualifications, assignments, and performance to ensure labor resources meet operational demands.

**Requirements**:
- Maintain employee and contractor profiles with personal information, certifications, and contact details.
- Assign roles and responsibilities aligned with port operations and terminal functions.
- Maintain a skill matrix to match personnel to required tasks and equipment.
- Manage contractor engagement details and integration with permanent staff planning.
- Track availability and planned absences such as leave and sick days.
- Monitor performance indicators and training requirements.
- Record training history, safety certifications, and renewal dates.
- Verify certifications and occupational health and safety compliance for active assignments.
- Support resource planning for surge demand and emergency call-in situations.

**Business Rules**:
- BR-L1.1: Personnel must possess valid certifications and safety training before assignment to regulated tasks.
- BR-L1.2: Contractor and permanent staff assignments must follow agreed labor engagement terms.
- BR-L1.3: Skill assignments must match the task requirements and regulatory certifications.
- BR-L1.4: Personnel with expired certifications cannot be assigned to roles requiring those credentials.
- BR-L1.5: Resource planning must account for fatigue management and maximum working hour limits.

**Workflow (WF-L1)**:
1. Register personnel with profiles, skills, and certification records.
2. Review resource requirements for upcoming operations and identify qualified personnel.
3. Assign roles, responsibilities, and availability windows.
4. Monitor certification expiry and training needs, updating records as required.
5. Reassign or supplement personnel in response to absences or demand surges.
6. Record performance and maintain the resource history for review.

**Exception Handling**:
- If a worker no-shows for a scheduled assignment → then reassign duties and alert shift supervision.
- If a certification expires during an active assignment → then remove the personnel from the regulated task and replace them.
- If a labor dispute arises between contractor and permanent staff → then escalate to HR and adjust assignments to maintain operations.
- If a sudden vessel arrival requires immediate crew mobilization → then activate standby resources and update assignment rosters.

**Priority**: Must Have

---

### FR-L2: Work Schedule Management
**Description**: Create and manage work schedules, including shift planning, dynamic adjustments, and compliance with labor regulations for port operations.

**Requirements**:
- Plan shifts for 8-hour, 12-hour, and 24-hour rotating schedules.
- Assign personnel to operations based on crew requirements and certification status.
- Manage overtime, extended shifts, and temporary duty assignments.
- Optimize schedules to balance operational needs, staffing levels, and labor regulations.
- Track absences, leave, sick days, and replacement requirements.
- Adjust schedules dynamically for emergencies, vessel delays, and unplanned labor shortages.
- Calculate labor cost estimates for scheduling decisions.
- Ensure schedule compliance with work hour regulations and fatigue management guidelines.
- Capture handover requirements and continuity needs between shifts.

**Business Rules**:
- BR-L2.1: Schedules must satisfy required staffing levels for operational and safety-critical functions.
- BR-L2.2: Overtime assignments must comply with labor regulation limits and be properly authorized.
- BR-L2.3: Shifts cannot exceed maximum allowable hours without explicit management approval.
- BR-L2.4: Absence coverage must be arranged before the shift begins.
- BR-L2.5: Emergency schedule adjustments must be documented and communicated promptly.

**Workflow (WF-L2)**:
1. Assess required staffing levels for upcoming operations and security coverage.
2. Build schedules with shifts, assignments, and required personnel.
3. Review schedules for compliance with work hours and certification needs.
4. Publish schedules and notify affected personnel.
5. Monitor attendance and operational execution during shifts.
6. Adjust schedules as needed for absences, emergencies, or unplanned workload changes.

**Exception Handling**:
- If a shift is understaffed due to absence → then source replacement personnel or adjust operations to maintain safety.
- If an operator reports fatigue or exceeds work-hour limits → then reassign duties and enforce rest periods.
- If an emergency call-in is required → then mobilize standby resources and update the schedule.
- If labor regulations change or a schedule violates compliance → then revise the schedule immediately and obtain required approvals.

**Priority**: Must Have

---

### FR-L3: Security Personnel Management
**Description**: Manage security personnel assignments, patrol scheduling, incident coordination, and access control support for port facilities.

**Requirements**:
- Assign security personnel to checkpoints, patrol routes, and access control duties.
- Schedule patrol routes and security coverage based on port activity and risk levels.
- Manage access control roles and authorization requirements.
- Log security incidents and response coordination details.
- Record security briefing histories and training completion.
- Reference CCTV and security monitoring support as part of coordination.
- Coordinate emergency response staffing for security incidents.
- Align security staffing with port operations, vessel arrivals, and cargo handling peaks.

**Business Rules**:
- BR-L3.1: Security assignments must meet required coverage levels for port zones and high-risk operations.
- BR-L3.2: Personnel assigned to security duties must hold required clearances and training.
- BR-L3.3: Incident logs must be maintained for each security event and response action.
- BR-L3.4: Emergency security response coordination takes precedence over routine patrol scheduling.
- BR-L3.5: Security staffing must be adjusted for sudden increases in vessel traffic or cargo security needs.

**Workflow (WF-L3)**:
1. Determine security coverage needs based on port schedule and risk assessments.
2. Assign security staff to patrols, access points, and control duties.
3. Communicate briefing details and shift responsibilities.
4. Monitor incident reports and coordinate response resources.
5. Log incident actions, outcomes, and follow-up requirements.
6. Review security staffing effectiveness and update future assignments.

**Exception Handling**:
- If a security incident requires additional personnel → then deploy standby security staff and escalate to management.
- If a patrol route cannot be covered due to staff shortage → then reassign duties and prioritize high-risk zones.
- If access control is compromised or a breach occurs → then initiate emergency response and reinforce staffing.
- If a security briefing is missed or incomplete → then delay assignment until the personnel are properly briefed.

**Priority**: Must Have

## 4. Global Business Rules
- G-BR1: Labor and resource assignments must be validated against certifications, role requirements, and labor regulations.
- G-BR2: Staffing decisions must preserve operational safety and compliance with MLC 2006 and occupational health and safety guidelines.
- G-BR3: All schedule changes, absences, and emergency reassignments must be documented for accountability.
- G-BR4: Personnel and security resources must be available for critical vessel arrivals, cargo operations, and emergency events.
- G-BR5: Contractor and permanent staff planning must be coordinated to prevent conflicts and ensure operational continuity.

## 5. Assumptions
- Personnel information, certifications, and availability data are maintained accurately by HR and operations teams.
- Labor regulations and safety requirements are defined and provided to scheduling teams.
- Emergency crew mobilization can be triggered to meet unplanned operational demands.
- Security staffing is aligned with port activity levels and vessel arrival patterns.
- Training and certification renewal schedules are monitored proactively.

## 6. Constraints
- Labor availability is constrained by certified personnel, regulatory work hour limits, and fatigue management.
- Shift planning is constrained by absence, leave, and unplanned sick events.
- Emergency responses may require reallocation of staff from routine duties.
- Contractor engagement terms may limit rapid redeployment or hourly changes.
- Security staffing must abide by clearance rules and zone-specific requirements.

## 7. Success Metrics
- Percentage of shifts staffed with qualified personnel as planned.
- Number of scheduling exceptions resolved without operational impact.
- Response time for emergency call-in and shift coverage changes.
- Percentage of active assignments with current certifications and compliance records.
- Number of labor-related incidents or disputes requiring escalation.
- Security incident response effectiveness and coverage compliance.
