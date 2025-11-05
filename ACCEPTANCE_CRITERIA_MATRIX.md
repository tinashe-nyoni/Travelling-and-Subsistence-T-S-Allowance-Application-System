# Acceptance Criteria Matrix
## Travelling and Subsistence (T&S) Allowance Application System

**Document Version:** 1.0  
**Date:** [Current Date]

---

## Overview

This document provides a comprehensive matrix of all acceptance criteria mapped to functional requirements, test cases, and validation status. It serves as a tracking tool for UAT execution and sign-off.

---

## Acceptance Criteria Matrix

### Employee Functions

#### Submit T&S Allowance Application

| AC ID | Acceptance Criteria | Functional Requirement | Test Case ID | Priority | Status | Notes |
|-------|-------------------|----------------------|--------------|----------|--------|-------|
| AC-EMP-001 | Employee can successfully submit a T&S Allowance application with all required fields | Submit T&S Application | TC-EMP-001, TC-EMP-002 | High | ⬜ | |
| AC-EMP-002 | System validates all mandatory fields (Employee ID, Departure Date, Departure Time, Departure City, Arrival Date, Arrival Time, Arrival City, Type of T&S Allowance) | Submit T&S Application | TC-EMP-003 | High | ⬜ | |
| AC-EMP-003 | System prevents submission if any mandatory field is missing | Submit T&S Application | TC-EMP-003 | High | ⬜ | |
| AC-EMP-004 | System validates date format and logical date relationships (Arrival Date ≥ Departure Date) | Submit T&S Application | TC-EMP-004, TC-EMP-005 | High | ⬜ | |
| AC-EMP-005 | System validates time format and logical time relationships (if same day, Arrival Time > Departure Time) | Submit T&S Application | TC-EMP-007 | Medium | ⬜ | |
| AC-EMP-006 | System calculates T&S Amount correctly for "Unapproved" type based on number of days ($135/day) | Submit T&S Application | TC-EMP-001, TC-CALC-001, TC-CALC-002, TC-CALC-005, TC-CALC-006 | High | ⬜ | |
| AC-EMP-007 | System calculates T&S Amount correctly for "Approved" type ($300/day) | Submit T&S Application | TC-EMP-002, TC-CALC-003, TC-CALC-004, TC-CALC-007 | High | ⬜ | |
| AC-EMP-008 | System displays calculated T&S Amount before submission | Submit T&S Application | TC-CALC-008 | High | ⬜ | |
| AC-EMP-009 | System saves application with status "pending" upon successful submission | Submit T&S Application | TC-EMP-001 | High | ⬜ | |
| AC-EMP-010 | System displays confirmation message after successful submission | Submit T&S Application | TC-EMP-001, TC-EMP-002 | High | ⬜ | |
| AC-EMP-011 | System sends email notification to employee upon submission (if implemented) | Submit T&S Application | [To be added if implemented] | Low | ⬜ | Optional |
| AC-EMP-012 | System prevents submission of duplicate applications for the same travel period | Submit T&S Application | TC-EMP-008 | Medium | ⬜ | |

#### View T&S Application Status

| AC ID | Acceptance Criteria | Functional Requirement | Test Case ID | Priority | Status | Notes |
|-------|-------------------|----------------------|--------------|----------|--------|-------|
| AC-EMP-013 | Employee can view list of their submitted T&S applications | View Application Status | TC-EMP-009, TC-EMP-010, TC-EMP-011 | High | ⬜ | |
| AC-EMP-014 | System displays application status (pending, approved, rejected) correctly | View Application Status | TC-EMP-009, TC-EMP-010, TC-EMP-011 | High | ⬜ | |
| AC-EMP-015 | Employee can filter/search their applications by date range or status | View Application Status | TC-EMP-012, TC-EMP-013, TC-EMP-014 | Medium | ⬜ | |
| AC-EMP-016 | System displays application details (Employee ID, dates, cities, type, amount, status) in readable format | View Application Status | TC-EMP-015 | High | ⬜ | |
| AC-EMP-017 | System displays rejection comments if application is rejected | View Application Status | TC-EMP-011 | High | ⬜ | |
| AC-EMP-018 | System displays approval/rejection date and supervisor information | View Application Status | TC-EMP-010, TC-EMP-011 | High | ⬜ | |

---

### Supervisor Functions

#### Review T&S Allowance Applications

| AC ID | Acceptance Criteria | Functional Requirement | Test Case ID | Priority | Status | Notes |
|-------|-------------------|----------------------|--------------|----------|--------|-------|
| AC-SUP-001 | Supervisor can view list of pending T&S applications for their team | Review Applications | TC-SUP-001 | High | ⬜ | |
| AC-SUP-002 | System displays all required application details (Employee ID, dates, cities, type, amount, days) | Review Applications | TC-SUP-002 | High | ⬜ | |
| AC-SUP-003 | Supervisor can filter applications by employee, date range, or status | Review Applications | TC-SUP-003, TC-SUP-004 | Medium | ⬜ | |
| AC-SUP-004 | Supervisor can sort applications by date, employee, or amount | Review Applications | TC-SUP-005 | Low | ⬜ | |
| AC-SUP-005 | System displays total number of pending applications | Review Applications | TC-SUP-001 | Medium | ⬜ | |
| AC-SUP-006 | Supervisor can view full application details in a single view | Review Applications | TC-SUP-002 | High | ⬜ | |

#### Approve/Reject T&S Application

| AC ID | Acceptance Criteria | Functional Requirement | Test Case ID | Priority | Status | Notes |
|-------|-------------------|----------------------|--------------|----------|--------|-------|
| AC-SUP-007 | Supervisor can approve a pending T&S application | Approve/Reject | TC-SUP-006 | High | ⬜ | |
| AC-SUP-008 | Supervisor can reject a pending T&S application | Approve/Reject | TC-SUP-007 | High | ⬜ | |
| AC-SUP-009 | System requires comments when supervisor rejects an application | Approve/Reject | TC-SUP-007, TC-SUP-008 | High | ⬜ | |
| AC-SUP-010 | System updates application status to "approved" upon approval | Approve/Reject | TC-SUP-006 | High | ⬜ | |
| AC-SUP-011 | System updates application status to "rejected" upon rejection | Approve/Reject | TC-SUP-007 | High | ⬜ | |
| AC-SUP-012 | System records supervisor's decision timestamp | Approve/Reject | TC-SUP-006, TC-SUP-007 | High | ⬜ | |
| AC-SUP-013 | System sends notification to employee upon approval (if implemented) | Approve/Reject | TC-SUP-006 | Low | ⬜ | Optional |
| AC-SUP-014 | System sends notification to employee upon rejection with comments (if implemented) | Approve/Reject | TC-SUP-007 | Low | ⬜ | Optional |
| AC-SUP-015 | Supervisor cannot approve/reject their own applications | Approve/Reject | TC-SUP-011 | High | ⬜ | |
| AC-SUP-016 | Supervisor can only view/approve applications for employees in their team | Approve/Reject | TC-SUP-010 | High | ⬜ | |
| AC-SUP-017 | System prevents approval/rejection of already processed applications | Approve/Reject | TC-SUP-009 | Medium | ⬜ | |

---

### System-Wide Criteria

| AC ID | Acceptance Criteria | Functional Requirement | Test Case ID | Priority | Status | Notes |
|-------|-------------------|----------------------|--------------|----------|--------|-------|
| AC-SYS-001 | System is accessible via web browser without installation | System-Wide | TC-INT-001 | High | ⬜ | |
| AC-SYS-002 | System displays clear error messages for invalid inputs | System-Wide | TC-EMP-003, TC-EMP-004, TC-EMP-005 | High | ⬜ | |
| AC-SYS-003 | System maintains data integrity (no data loss or corruption) | System-Wide | TC-INT-004 | High | ⬜ | |
| AC-SYS-004 | System handles concurrent access appropriately | System-Wide | TC-INT-003 | Medium | ⬜ | |
| AC-SYS-005 | System provides appropriate user authentication and authorization | System-Wide | TC-INT-001, TC-SUP-010, TC-SUP-011 | High | ⬜ | |
| AC-SYS-006 | System displays appropriate messages for session timeout | System-Wide | TC-INT-002 | Medium | ⬜ | |
| AC-SYS-007 | System is responsive and user-friendly | System-Wide | [User Experience Testing] | Medium | ⬜ | Subjective |

---

## Status Legend

- ⬜ **Not Started** - Acceptance criteria not yet validated
- 🟡 **In Progress** - Currently being tested
- ✅ **Passed** - Acceptance criteria met
- ❌ **Failed** - Acceptance criteria not met
- ⚠️ **Blocked** - Cannot be tested due to blocking issue
- ⏸️ **Deferred** - Testing deferred to later phase

---

## Summary Statistics

| Category | Total | Not Started | In Progress | Passed | Failed | Blocked | Deferred |
|----------|-------|-------------|------------|-------|--------|---------|----------|
| Employee Functions | 18 | 18 | 0 | 0 | 0 | 0 | 0 |
| Supervisor Functions | 17 | 17 | 0 | 0 | 0 | 0 | 0 |
| System-Wide | 7 | 7 | 0 | 0 | 0 | 0 | 0 |
| **TOTAL** | **42** | **42** | **0** | **0** | **0** | **0** | **0** |

---

## Validation Process

1. **Assign Test Cases:** Each acceptance criteria is mapped to specific test cases
2. **Execute Tests:** Test cases are executed by UAT panelists
3. **Update Status:** Status is updated in this matrix as tests are executed
4. **Track Defects:** Failed criteria are linked to defect IDs
5. **Retest:** After defect fixes, retest and update status
6. **Sign-off:** Once all criteria pass, obtain sign-off

---

## Sign-off Requirements

For UAT to be considered complete:
- ✅ All High Priority acceptance criteria must be **Passed**
- ✅ ≥ 95% of all acceptance criteria must be **Passed**
- ✅ All Critical and High priority defects must be resolved
- ✅ Zero P1 (Critical) defects remaining

---

## Notes

- Acceptance criteria marked as "Optional" (AC-EMP-011, AC-SUP-013, AC-SUP-014) are not mandatory for sign-off if not implemented
- AC-SYS-007 (User-friendly) requires subjective evaluation by UAT panelists
- Update this matrix regularly during UAT execution
- Keep defect IDs linked to failed acceptance criteria for traceability

---

**End of Acceptance Criteria Matrix**

