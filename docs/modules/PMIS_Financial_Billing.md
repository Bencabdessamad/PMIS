# Financial & Billing Management

## 1. Overview
The Financial & Billing Management module governs port tariff configuration, invoice generation, payment tracking, and financial reporting. It supports accurate charge calculation, compliance with tax and audit requirements, and timely resolution of commercial exceptions.

## 2. Scope
### 2.1 In Scope
- Definition and management of port tariff rules, fee structures, discounts, and seasonal pricing.
- Generation and archival of invoices with detailed charge breakdowns, payment terms, and tax calculations.
- Tracking payments, partial settlements, aging analysis, disputes, and reconciliation activities.
- Financial reporting for revenues, costs, cash flow, and compliance with audit requirements.

### 2.2 Out of Scope
- Operational planning of vessel, berth, cargo, or equipment activities beyond billing data consumption.
- Direct processing of bank transactions or payment gateway implementation.
- Detailed tax system configuration and external accounting system posting.
- Labor costing beyond equipment rental and service charge capture.

## 3. Functional Requirements

### FR-F1: Tariff Management
**Description**: Manage port tariffs, pricing rules, and charge structures for vessels, cargo, berths, and equipment to support accurate billing and commercial policy enforcement.

**Requirements**:
- Define port dues calculation rules for vessels and port services.
- Manage vessel fee structures based on size, weight, draft, or other operational metrics.
- Define cargo handling charges and storage or warehouse fees.
- Set berth rental fees and equipment rental rates.
- Capture seasonal pricing variations and holiday surcharges.
- Manage discount rules, promotional rates, and special customer agreements.
- Support commission structures for agents and third-party service providers.
- Validate tariff application against service eligibility and commercial rules.
- Record tariff versions and effective date history for audit and dispute resolution.

**Business Rules**:
- BR-F1.1: Tariffs must be versioned and applied according to the effective date in force at the time of service.
- BR-F1.2: Vessel and cargo charges must be calculated from agreed structures and validated against operational data.
- BR-F1.3: Discounts and promotions must not exceed policy limits and require proper authorization.
- BR-F1.4: Agent commissions must be calculated from established commission structures and documented.
- BR-F1.5: Seasonal or special rates must be clearly defined and applied consistently.

**Workflow (WF-F1)**:
1. Define tariff categories and service charge components.
2. Specify pricing rules for vessels, cargo, berth, equipment, and ancillary services.
3. Establish discount, promotion, and commission rules.
4. Validate tariff rules against commercial terms and port policy.
5. Publish tariff schedules and maintain change history.
6. Review and update tariffs for regulatory or market changes.

**Exception Handling**:
- If a tariff rule is missing for a service → then prevent invoice generation and flag the service for tariff review.
- If a discount exceeds authorized limits → then reject the discount and notify finance.
- If a tariff effective date is incorrect → then correct the date and recalculate affected charges.
- If a commission structure is not defined for an agent-required service → then withhold the charge until the structure is established.

**Priority**: Must Have

---

### FR-F2: Invoice Generation
**Description**: Generate accurate invoices from operational activity, with detailed line items, payment terms, and tax calculations, while managing versioning and transmission.

**Requirements**:
- Generate invoices automatically from operations and chargeable services.
- Provide line item details for vessel dues, cargo handling, storage, berth rental, equipment rental, and ancillary services.
- Support configurable invoice templates for different customer groups.
- Manage payment terms, due dates, credit limits, and early payment discounts.
- Assign invoice numbers and archive invoice records for audit.
- Support multi-currency invoices with appropriate currency selection rules.
- Calculate taxes such as VAT, GST, and other applicable duties at the business level.
- Support invoice distribution to customers by email or EDI.
- Track invoice revisions, reissues, and credit/debit notes.

**Business Rules**:
- BR-F2.1: Invoices must reflect actual services rendered and approved tariff rules.
- BR-F2.2: Payment terms and due dates must be applied based on customer agreements.
- BR-F2.3: Multi-currency invoices must use the agreed currency for the customer and indicate exchange rules.
- BR-F2.4: Taxes must be calculated according to applicable financial regulations and included in invoice totals.
- BR-F2.5: Invoice revisions must preserve audit trail and reference original document numbers.

**Workflow (WF-F2)**:
1. Collect chargeable service data from vessel, cargo, berth, equipment, and customs operations.
2. Apply tariff rules, discounts, taxes, and payment terms.
3. Generate invoice draft and review for accuracy.
4. Issue the invoice to the customer and archive the final document.
5. Track invoice status and handle revisions or credit/debit adjustments.
6. Retain invoice history for financial audit purposes.

**Exception Handling**:
- If an invoice contains disputed or incorrect charges → then hold the invoice, investigate the issue, and issue a corrected invoice if required.
- If customer currency or tax details are missing → then prevent issuance until the information is confirmed.
- If an invoice is rejected by EDI transmission or email delivery fails → then retry transmission and notify finance.
- If an invoice must be reissued due to changes after issue → then create a new version with audit references to the original.

**Priority**: Must Have

---

### FR-F3: Payment Management
**Description**: Track payments, manage outstanding balances, handle partial payments and disputes, and reconcile receipts against invoices to support port cash collection and credit control.

**Requirements**:
- Support multiple payment methods including bank transfer, credit card, and cheque.
- Generate payment receipts and apply payments against invoices.
- Track outstanding payment balances and invoice aging.
- Handle partial payments and advance payments.
- Reconcile payments with invoices and financial records.
- Monitor credit limits and customer exposure.
- Generate payment reminders and overdue notifications.
- Support dispute resolution workflows for payments and invoice discrepancies.
- Capture refunds, adjustments, and write-offs as business events.

**Business Rules**:
- BR-F3.1: Payments must be matched to invoices and applied according to the customer’s agreed terms.
- BR-F3.2: Partial payments should be allocated correctly and outstanding balances recalculated.
- BR-F3.3: Customers cannot exceed approved credit limits without explicit finance approval.
- BR-F3.4: Overdue invoices require reminders and may trigger late payment penalties or holds.
- BR-F3.5: Disputes must be recorded and resolved before final payment settlement.

**Workflow (WF-F3)**:
1. Record incoming payments and validate against outstanding invoices.
2. Apply payments to the correct invoice(s) and update the customer balance.
3. Monitor aged receivables and identify overdue accounts.
4. Issue reminders, request payment, or escalate as appropriate.
5. Manage disputes by documenting issues, investigating, and adjusting invoices if necessary.
6. Capture refunds or write-offs when required and update financial records.

**Exception Handling**:
- If a payment amount is less than the invoice total → then allocate the partial payment and update the remaining balance.
- If a customer exceeds their credit limit → then halt further service billing and notify credit control.
- If a payment is disputed → then log dispute details, hold collection activity, and resolve the discrepancy.
- If a vessel departs prior to full payment → then record outstanding receivables and enforce collection policies.

**Priority**: Must Have

---

### FR-F4: Financial Reporting
**Description**: Produce financial reports and analytics that summarize revenue, cost, cash flow, and compliance metrics to support port management and audit requirements.

**Requirements**:
- Generate revenue reports by customer, vessel, cargo type, and service category.
- Provide utilization versus revenue analysis for berths, equipment, and terminal services.
- Support cost center reporting and profit margin analysis.
- Generate cash flow forecasting and receivables aging reports.
- Deliver financial KPI dashboards for operational and executive oversight.
- Maintain audit trail for all financial transactions.
- Support period-end closing and reporting requirements.
- Provide financial insight into disputed invoices, penalties, refunds, and credit exposure.

**Business Rules**:
- BR-F4.1: Financial reports must use validated invoice and payment data.
- BR-F4.2: Cash flow forecasts should account for outstanding invoices, payment terms, and known disputes.
- BR-F4.3: Audit trails must be preserved for every transaction, adjustment, and report.
- BR-F4.4: Period-end reports must align with fiscal closing schedules and regulatory reporting periods.
- BR-F4.5: Reports on disputed invoices, penalties, and refunds must be available for commercial review.

**Workflow (WF-F4)**:
1. Consolidate invoice, payment, aging, and adjustment data.
2. Generate standard financial reports and dashboards.
3. Review and validate report results against operational and accounting expectations.
4. Distribute financial summaries to stakeholders and management.
5. Support audit and period-end closing activities with retained documentation.
6. Use reporting insights to identify revenue leakage, overdue accounts, and pricing performance.

**Exception Handling**:
- If report data is inconsistent with financial records → then investigate source discrepancies and correct underlying data.
- If a period-end close reveals unresolved disputes or uncleared payments → then escalate to finance leadership for resolution.
- If tax or audit requirements change → then update reporting rules and ensure compliance.
- If a report cannot be generated due to missing data → then identify the gap and provide interim manual support.

**Priority**: Must Have

## 4. Global Business Rules
- G-BR1: Billing and finance must be driven by operational activity, tariff rules, and agreed commercial terms.
- G-BR2: All charges, payments, and adjustments must be auditable for financial and regulatory review.
- G-BR3: Outstanding receivables and credit exposure must be monitored and managed proactively.
- G-BR4: Tax and audit compliance must be embedded in invoice creation and financial reporting.
- G-BR5: Disputes, penalties, refunds, and exceptional events must be documented and reconciled.

## 5. Assumptions
- Operational data for charges is accurate and available in a timely manner.
- Customers have agreed payment terms and credit arrangements before services are rendered.
- Finance teams have access to required tax and regulatory guidance.
- Dispute resolution processes are in place between port commercial teams and customers.
- Financial reports are used to inform commercial decision-making and cash collection.

## 6. Constraints
- Billing is constrained by the accuracy of service activity data and tariff definitions.
- Payment processing is constrained by customer credit terms, currency agreements, and bank clearance times.
- Financial reporting is constrained by audit requirements and data completeness.
- Disputes and corrective actions can delay revenue recognition and cash flow.
- Regulatory tax and customs duties impose compliance requirements on invoicing.

## 7. Success Metrics
- Percentage of invoices issued accurately without subsequent revision.
- Days sales outstanding (DSO) and reduction in aged receivables.
- Number of disputed invoices resolved within agreed timeframes.
- Percentage of payments reconciled successfully against invoices.
- Accuracy of cash flow forecasts against actual collections.
- Compliance with audit and tax reporting requirements.
