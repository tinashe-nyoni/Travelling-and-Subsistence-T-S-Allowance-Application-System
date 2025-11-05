# User Acceptance Testing (UAT) Plan
## Travelling and Subsistence (T&S) Allowance Application System

**Document Version:** 1.0  
**Date:** November 5, 2025  
**Prepared By:** UAT Team  
**Status:** Draft

---

## Table of Contents.

1. [Introduction](#introduction)
2. [UAT Objectives](#uat-objectives)
3. [Scope and Out of Scope](#scope-and-out-of-scope)
4. [Test Environment](#test-environment)
5. [Test Team Roles and Responsibilities](#test-team-roles-and-responsibilities)
6. [UAT Schedule](#uat-schedule)
7. [Acceptance Criteria](#acceptance-criteria)
8. [Test Cases Overview](#test-cases-overview)
9. [Test Data Requirements](#test-data-requirements)
10. [Defect Management](#defect-management)
11. [UAT Entry and Exit Criteria](#uat-entry-and-exit-criteria)
12. [Sign-off Process](#sign-off-process)
13. [Appendices](#appendices)

---

## 1. Introduction

### 1.1 Purpose
This User Acceptance Testing (UAT) Plan document defines the strategy, approach, and methodology for conducting User Acceptance Testing of the Travelling and Subsistence (T&S) Allowance Application System. The purpose of UAT is to validate that the system meets the business requirements and is ready for production deployment.

### 1.2 Background
The T&S Allowance Application System is designed to facilitate online submission, tracking, and approval of Travelling and Subsistence Allowance applications. The system enables employees to submit T&S applications and allows supervisors to review and approve/reject these applications.

### 1.3 Document Audience
- Development Team
- UAT Panelists (Employees and Supervisors)
- Project Managers
- Business Stakeholders
- Quality Assurance Team

---

## 2. UAT Objectives

### 2.1 Primary Objectives
1. Verify that all functional requirements are implemented correctly
2. Validate that the system meets user expectations and business needs
3. Ensure the system is user-friendly and intuitive
4. Confirm that T&S calculations are accurate
5. Validate workflow processes (submission → review → approval/rejection)
6. Verify notification mechanisms (if implemented)

### 2.2 Success Criteria
- All critical acceptance criteria are met
- Zero critical defects remain unresolved
- User satisfaction score ≥ 85%
- All test cases pass with ≥ 95% pass rate
- System performance meets specified requirements

---

## 3. Scope and Out of Scope

### 3.1 In Scope
- Employee submission of T&S Allowance applications
- T&S amount calculation (Unapproved and Approved types)
- Supervisor review of applications
- Supervisor approval/rejection of applications
- Application status tracking
- Employee viewing of application status
- Basic notification mechanisms (if implemented)

### 3.2 Out of Scope
- Performance testing (load/stress testing)
- Security penetration testing
- Integration with external systems (unless specified)
- Mobile application testing (if not part of requirements)
- Advanced reporting and analytics

---

## 4. Test Environment

### 4.1 Environment Requirements
- **URL:** [To be provided by development team]
- **Browser Compatibility:** Chrome, Firefox, Edge (latest versions)
- **Database:** Test database with sample data
- **User Accounts:** Test accounts for Employees and Supervisors

### 4.2 Test Data
- Pre-configured employee accounts
- Pre-configured supervisor accounts
- Sample T&S applications for reference
- See **Test Data Requirements** section for details

---

## 5. Test Team Roles and Responsibilities

### 5.1 UAT Panelists
- **Employees (2-3 representatives):** Test employee functions
- **Supervisors (2-3 representatives):** Test supervisor functions

### 5.2 Development Team
- Provide technical support during UAT
- Fix defects identified during testing
- Provide test environment access and credentials

### 5.3 UAT Coordinator
- Coordinate UAT activities
- Track test execution progress
- Manage defect resolution
- Prepare UAT reports

---

## 6. UAT Schedule

| Phase | Activity | Duration | Responsible |
|-------|----------|----------|-------------|
| Phase 1 | UAT Preparation | 2 days | UAT Coordinator |
| Phase 2 | Test Execution | 5 days | UAT Panelists |
| Phase 3 | Defect Resolution | 3 days | Development Team |
| Phase 4 | Re-testing | 2 days | UAT Panelists |
| Phase 5 | UAT Sign-off | 1 day | Stakeholders |

**Total Duration:** 13 working days

---

## 7. Acceptance Criteria

### 7.1 Employee Functions

#### 7.1.1 Submit T&S Allowance Application

**AC-EMP-001:** Employee can successfully submit a T&S Allowance application with all required fields.

**AC-EMP-002:** System validates all mandatory fields (Employee ID, Departure Date, Departure Time, Departure City, Arrival Date, Arrival Time, Arrival City, Type of T&S Allowance).

**AC-EMP-003:** System prevents submission if any mandatory field is missing.

**AC-EMP-004:** System validates date format and logical date relationships (Arrival Date ≥ Departure Date).

**AC-EMP-005:** System validates time format and logical time relationships (if same day, Arrival Time > Departure Time).

**AC-EMP-006:** System calculates T&S Amount correctly for "Unapproved" type based on number of days:
   - Breakfast: $15 per day
   - Lunch: $20 per day
   - Dinner: $25 per day
   - Accommodation: $75 per day
   - Total per day: $135

**AC-EMP-007:** System calculates T&S Amount correctly for "Approved" type: $300 per day.

**AC-EMP-008:** System displays calculated T&S Amount before submission.

**AC-EMP-009:** System saves application with status "pending" upon successful submission.

**AC-EMP-010:** System displays confirmation message after successful submission.

**AC-EMP-011:** System sends email notification to employee upon submission (if implemented).

**AC-EMP-012:** System prevents submission of duplicate applications for the same travel period.

#### 7.1.2 View T&S Application Status

**AC-EMP-013:** Employee can view list of their submitted T&S applications.

**AC-EMP-014:** System displays application status (pending, approved, rejected) correctly.

**AC-EMP-015:** Employee can filter/search their applications by date range or status.

**AC-EMP-016:** System displays application details (Employee ID, dates, cities, type, amount, status) in readable format.

**AC-EMP-017:** System displays rejection comments if application is rejected.

**AC-EMP-018:** System displays approval/rejection date and supervisor information.

### 7.2 Supervisor Functions

#### 7.2.1 Review T&S Allowance Applications

**AC-SUP-001:** Supervisor can view list of pending T&S applications for their team.

**AC-SUP-002:** System displays all required application details:
   - Employee ID
   - Departure Date and Time
   - Arrival Date and Time
   - Departure City
   - Arrival City
   - Type of T&S Allowance
   - Calculated T&S Amount
   - Number of days

**AC-SUP-003:** Supervisor can filter applications by employee, date range, or status.

**AC-SUP-004:** Supervisor can sort applications by date, employee, or amount.

**AC-SUP-005:** System displays total number of pending applications.

**AC-SUP-006:** Supervisor can view full application details in a single view.

#### 7.2.2 Approve/Reject T&S Application

**AC-SUP-007:** Supervisor can approve a pending T&S application.

**AC-SUP-008:** Supervisor can reject a pending T&S application.

**AC-SUP-009:** System requires comments when supervisor rejects an application.

**AC-SUP-010:** System updates application status to "approved" upon approval.

**AC-SUP-011:** System updates application status to "rejected" upon rejection.

**AC-SUP-012:** System records supervisor's decision timestamp.

**AC-SUP-013:** System sends notification to employee upon approval (if implemented).

**AC-SUP-014:** System sends notification to employee upon rejection with comments (if implemented).

**AC-SUP-015:** Supervisor cannot approve/reject their own applications.

**AC-SUP-016:** Supervisor can only view/approve applications for employees in their team.

**AC-SUP-017:** System prevents approval/rejection of already processed applications.

### 7.3 System-Wide Criteria

**AC-SYS-001:** System is accessible via web browser without installation.

**AC-SYS-002:** System displays clear error messages for invalid inputs.

**AC-SYS-003:** System maintains data integrity (no data loss or corruption).

**AC-SYS-004:** System handles concurrent access appropriately.

**AC-SYS-005:** System provides appropriate user authentication and authorization.

**AC-SYS-006:** System displays appropriate messages for session timeout.

**AC-SYS-007:** System is responsive and user-friendly.

---

## 8. Test Cases Overview

A detailed test cases document is provided separately (see **TEST_CASES.md**). The test cases cover:

- **Employee Test Cases:** 25+ test scenarios
- **Supervisor Test Cases:** 20+ test scenarios
- **System Integration Test Cases:** 10+ test scenarios
- **Calculation Test Cases:** 15+ test scenarios

Total: **70+ test cases**

---

## 9. Test Data Requirements

### 9.1 Employee Test Accounts
- Employee ID: EMP001, EMP002, EMP003
- Each with valid authentication credentials

### 9.2 Supervisor Test Accounts
- Supervisor ID: SUP001, SUP002
- Each with valid authentication credentials
- Each assigned to manage specific employee groups

### 9.3 Sample Travel Scenarios
- Single day travel (same departure and arrival date)
- Multi-day travel (2-5 days)
- Weekend travel
- Cross-border travel scenarios

### 9.4 Test Data Setup
- Pre-existing pending applications for supervisors to review
- Mix of approved and rejected applications for status viewing
- Applications with various T&S types (Unapproved and Approved)

---

## 10. Defect Management

### 10.1 Defect Severity Levels

**Critical (P1):** System crash, data loss, security breach, calculation errors
- **Resolution Time:** Immediate (within 24 hours)

**High (P2):** Major functionality not working, workflow blocked
- **Resolution Time:** 48 hours

**Medium (P3):** Minor functionality issue, workaround available
- **Resolution Time:** 5 days

**Low (P4):** Cosmetic issues, minor UI improvements
- **Resolution Time:** Next release

### 10.2 Defect Tracking
- All defects must be logged in the defect tracking system
- Defect must include: Description, Steps to Reproduce, Expected Result, Actual Result, Severity, Screenshots (if applicable)

### 10.3 Defect Resolution Process
1. UAT Panelist identifies defect
2. Defect logged in tracking system
3. Development team reviews and assigns priority
4. Development team fixes defect
5. Defect retested by UAT Panelist
6. Defect marked as closed if resolved

---

## 11. UAT Entry and Exit Criteria

### 11.1 Entry Criteria
- ✅ System Development completed
- ✅ Unit Testing completed
- ✅ System Testing completed
- ✅ Test environment is ready and accessible
- ✅ Test data is prepared
- ✅ UAT team is identified and available
- ✅ UAT plan is approved

### 11.2 Exit Criteria
- ✅ All critical (P1) and high (P2) priority defects are resolved
- ✅ ≥ 95% of test cases are executed
- ✅ ≥ 95% of test cases pass
- ✅ All acceptance criteria are met
- ✅ UAT sign-off obtained from stakeholders
- ✅ UAT report is prepared and approved

---

## 12. Sign-off Process

### 12.1 Sign-off Requirements
UAT will be considered complete when:
1. All acceptance criteria are validated
2. All critical and high priority defects are resolved
3. UAT report is approved
4. Sign-off is obtained from:
   - UAT Panelists (Employee and Supervisor representatives)
   - Project Manager
   - Business Stakeholder

### 12.2 Sign-off Document
A formal UAT Sign-off document will be prepared with:
- Test execution summary
- Defect summary
- Acceptance criteria status
- Recommendations
- Signatures from all stakeholders

---

## 13. Appendices

### Appendix A: T&S Calculation Reference

#### Unapproved T&S Allowance
- Breakfast: $15 per day
- Lunch: $20 per day
- Dinner: $25 per day
- Accommodation: $75 per day
- **Total per day: $135**

**Calculation Formula:**
```
Total Unapproved Amount = Number of Days × $135
```

#### Approved T&S Allowance
- **Total per day: $300**

**Calculation Formula:**
```
Total Approved Amount = Number of Days × $300
```

#### Number of Days Calculation
- Count all days from Departure Date to Arrival Date (inclusive)
- Example: Departure Date = 2024-01-01, Arrival Date = 2024-01-03
  - Number of Days = 3

### Appendix B: Test Environment Access
- URL: [To be provided]
- Credentials: [To be provided separately]

### Appendix C: Contact Information
- UAT Coordinator: [Name and Email]
- Development Team Lead: [Name and Email]
- Project Manager: [Name and Email]

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 5, 2025 | UAT Team | Initial version |

---

**End of UAT Plan**

