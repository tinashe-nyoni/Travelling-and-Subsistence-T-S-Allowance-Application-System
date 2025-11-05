# Test Cases Document
## Travelling and Subsistence (T&S) Allowance Application System

**Document Version:** 1.0  
**Date:** [Current Date]  
**Total Test Cases:** 70+

---

## Table of Contents

1. [Employee Test Cases](#employee-test-cases)
2. [Supervisor Test Cases](#supervisor-test-cases)
3. [Calculation Test Cases](#calculation-test-cases)
4. [System Integration Test Cases](#system-integration-test-cases)
5. [Test Case Execution Template](#test-case-execution-template)

---

## Employee Test Cases

### TC-EMP-001: Submit T&S Application - Valid Unapproved Type
**Priority:** High  
**Test Objective:** Verify employee can submit a valid T&S application with Unapproved type.

**Preconditions:**
- Employee is logged into the system
- Employee has valid Employee ID

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Enter Employee ID: EMP001
3. Enter Departure Date: 2024-02-01
4. Enter Departure Time: 08:00
5. Enter Departure City: New York
6. Enter Arrival Date: 2024-02-03
7. Enter Arrival Time: 18:00
8. Enter Arrival City: Los Angeles
9. Select Type of T&S Allowance: Unapproved
10. Verify calculated T&S Amount: $405 (3 days × $135)
11. Click "Submit" button

**Expected Result:**
- Application is submitted successfully
- Confirmation message is displayed
- Application status is "pending"
- T&S Amount is calculated correctly as $405

**Acceptance Criteria:** AC-EMP-001, AC-EMP-006, AC-EMP-009, AC-EMP-010

---

### TC-EMP-002: Submit T&S Application - Valid Approved Type
**Priority:** High  
**Test Objective:** Verify employee can submit a valid T&S application with Approved type.

**Preconditions:**
- Employee is logged into the system

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Enter all required fields with valid data
3. Select Type of T&S Allowance: Approved
4. Enter Departure Date: 2024-02-01
5. Enter Arrival Date: 2024-02-02
6. Verify calculated T&S Amount: $600 (2 days × $300)
7. Click "Submit" button

**Expected Result:**
- Application is submitted successfully
- T&S Amount is calculated correctly as $600
- Confirmation message is displayed

**Acceptance Criteria:** AC-EMP-001, AC-EMP-007, AC-EMP-010

---

### TC-EMP-003: Submit T&S Application - Missing Mandatory Fields
**Priority:** High  
**Test Objective:** Verify system validates mandatory fields.

**Preconditions:**
- Employee is logged into the system

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Leave Employee ID field empty
3. Click "Submit" button

**Expected Result:**
- Submission is prevented
- Error message displayed: "Employee ID is required"
- Field is highlighted in red

**Acceptance Criteria:** AC-EMP-003

---

### TC-EMP-004: Submit T&S Application - Invalid Date Format
**Priority:** Medium  
**Test Objective:** Verify system validates date format.

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Enter Departure Date: "01/02/2024" (invalid format)
3. Attempt to submit

**Expected Result:**
- System displays error message: "Invalid date format. Please use YYYY-MM-DD"
- Submission is prevented

**Acceptance Criteria:** AC-EMP-004

---

### TC-EMP-005: Submit T&S Application - Arrival Date Before Departure Date
**Priority:** High  
**Test Objective:** Verify system validates logical date relationships.

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Enter Departure Date: 2024-02-05
3. Enter Arrival Date: 2024-02-03 (before departure)
4. Click "Submit" button

**Expected Result:**
- Submission is prevented
- Error message displayed: "Arrival Date cannot be before Departure Date"

**Acceptance Criteria:** AC-EMP-004

---

### TC-EMP-006: Submit T&S Application - Same Day Travel
**Priority:** Medium  
**Test Objective:** Verify system handles same day travel correctly.

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Enter Departure Date: 2024-02-01
3. Enter Departure Time: 08:00
4. Enter Arrival Date: 2024-02-01 (same day)
5. Enter Arrival Time: 20:00
6. Select Type: Unapproved
7. Verify calculated amount

**Expected Result:**
- System calculates 1 day correctly
- T&S Amount = $135 for Unapproved type
- Application can be submitted

**Acceptance Criteria:** AC-EMP-006

---

### TC-EMP-007: Submit T&S Application - Time Validation Same Day
**Priority:** Medium  
**Test Objective:** Verify time validation for same day travel.

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Enter Departure Date: 2024-02-01
3. Enter Departure Time: 20:00
4. Enter Arrival Date: 2024-02-01
5. Enter Arrival Time: 08:00 (before departure time)
6. Click "Submit"

**Expected Result:**
- Error message: "Arrival Time must be after Departure Time for same day travel"
- Submission prevented

**Acceptance Criteria:** AC-EMP-005

---

### TC-EMP-008: Submit T&S Application - Duplicate Application Prevention
**Priority:** Medium  
**Test Objective:** Verify system prevents duplicate applications.

**Preconditions:**
- Employee has already submitted an application for 2024-02-01 to 2024-02-03

**Test Steps:**
1. Navigate to "Submit T&S Application" page
2. Enter same Employee ID and same travel dates
3. Click "Submit"

**Expected Result:**
- Error message: "An application already exists for this travel period"
- Submission prevented

**Acceptance Criteria:** AC-EMP-012

---

### TC-EMP-009: View Application Status - Pending Status
**Priority:** High  
**Test Objective:** Verify employee can view pending application status.

**Preconditions:**
- Employee has submitted an application with status "pending"

**Test Steps:**
1. Navigate to "My Applications" page
2. Locate the pending application
3. View application details

**Expected Result:**
- Application is displayed in the list
- Status shows as "pending"
- All application details are visible

**Acceptance Criteria:** AC-EMP-013, AC-EMP-014

---

### TC-EMP-010: View Application Status - Approved Status
**Priority:** High  
**Test Objective:** Verify employee can view approved application status.

**Preconditions:**
- Employee has an approved application

**Test Steps:**
1. Navigate to "My Applications" page
2. Locate the approved application
3. View application details

**Expected Result:**
- Status shows as "approved"
- Approval date is displayed
- Supervisor information is displayed (if available)

**Acceptance Criteria:** AC-EMP-014, AC-EMP-018

---

### TC-EMP-011: View Application Status - Rejected Status
**Priority:** High  
**Test Objective:** Verify employee can view rejected application with comments.

**Preconditions:**
- Employee has a rejected application

**Test Steps:**
1. Navigate to "My Applications" page
2. Locate the rejected application
3. View application details

**Expected Result:**
- Status shows as "rejected"
- Rejection comments are displayed
- Rejection date is displayed

**Acceptance Criteria:** AC-EMP-014, AC-EMP-017

---

### TC-EMP-012: Filter Applications by Status
**Priority:** Medium  
**Test Objective:** Verify filtering functionality.

**Test Steps:**
1. Navigate to "My Applications" page
2. Select filter: "Status = Pending"
3. Click "Apply Filter"

**Expected Result:**
- Only pending applications are displayed
- Filter is applied correctly

**Acceptance Criteria:** AC-EMP-015

---

### TC-EMP-013: Filter Applications by Date Range
**Priority:** Medium  
**Test Objective:** Verify date range filtering.

**Test Steps:**
1. Navigate to "My Applications" page
2. Select date range filter: From 2024-01-01 to 2024-01-31
3. Click "Apply Filter"

**Expected Result:**
- Only applications within the date range are displayed

**Acceptance Criteria:** AC-EMP-015

---

### TC-EMP-014: Search Applications
**Priority:** Low  
**Test Objective:** Verify search functionality.

**Test Steps:**
1. Navigate to "My Applications" page
2. Enter search term in search box
3. Click "Search"

**Expected Result:**
- Relevant applications are displayed based on search criteria

**Acceptance Criteria:** AC-EMP-015

---

### TC-EMP-015: View Application Details
**Priority:** High  
**Test Objective:** Verify all application details are displayed correctly.

**Test Steps:**
1. Navigate to "My Applications" page
2. Click on an application to view details

**Expected Result:**
- All details are displayed:
  - Employee ID
  - Departure Date and Time
  - Arrival Date and Time
  - Departure City
  - Arrival City
  - Type of T&S Allowance
  - T&S Amount
  - Status
  - Dates (submission, approval/rejection)

**Acceptance Criteria:** AC-EMP-016

---

## Supervisor Test Cases

### TC-SUP-001: View Pending Applications List
**Priority:** High  
**Test Objective:** Verify supervisor can view list of pending applications.

**Preconditions:**
- Supervisor is logged into the system
- There are pending applications for supervisor's team

**Test Steps:**
1. Navigate to "Pending Applications" page
2. View the list of applications

**Expected Result:**
- List of pending applications is displayed
- Total count of pending applications is shown
- Each application shows key information (Employee ID, dates, amount)

**Acceptance Criteria:** AC-SUP-001, AC-SUP-005

---

### TC-SUP-002: View Application Details for Review
**Priority:** High  
**Test Objective:** Verify supervisor can view complete application details.

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Click on an application to view details

**Expected Result:**
- All application details are displayed:
  - Employee ID
  - Departure Date and Time
  - Arrival Date and Time
  - Departure City
  - Arrival City
  - Type of T&S Allowance
  - Calculated T&S Amount
  - Number of days

**Acceptance Criteria:** AC-SUP-002, AC-SUP-006

---

### TC-SUP-003: Filter Applications by Employee
**Priority:** Medium  
**Test Objective:** Verify supervisor can filter applications by employee.

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Select filter: Employee ID = EMP001
3. Click "Apply Filter"

**Expected Result:**
- Only applications from EMP001 are displayed

**Acceptance Criteria:** AC-SUP-003

---

### TC-SUP-004: Filter Applications by Date Range
**Priority:** Medium  
**Test Objective:** Verify date range filtering.

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Select date range: From 2024-01-01 to 2024-01-31
3. Click "Apply Filter"

**Expected Result:**
- Only applications within date range are displayed

**Acceptance Criteria:** AC-SUP-003

---

### TC-SUP-005: Sort Applications by Date
**Priority:** Low  
**Test Objective:** Verify sorting functionality.

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Click on "Departure Date" column header to sort

**Expected Result:**
- Applications are sorted by departure date (ascending/descending)

**Acceptance Criteria:** AC-SUP-004

---

### TC-SUP-006: Approve Application
**Priority:** High  
**Test Objective:** Verify supervisor can approve an application.

**Preconditions:**
- Supervisor is viewing a pending application

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Select an application
3. Click "Approve" button
4. Confirm approval in popup (if applicable)

**Expected Result:**
- Application status changes to "approved"
- Approval timestamp is recorded
- Application is removed from pending list
- Employee is notified (if implemented)

**Acceptance Criteria:** AC-SUP-007, AC-SUP-010, AC-SUP-012, AC-SUP-013

---

### TC-SUP-007: Reject Application with Comments
**Priority:** High  
**Test Objective:** Verify supervisor can reject an application with comments.

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Select an application
3. Click "Reject" button
4. Enter rejection comments: "Travel dates not approved by management"
5. Click "Confirm Rejection"

**Expected Result:**
- Application status changes to "rejected"
- Rejection comments are saved
- Rejection timestamp is recorded
- Employee is notified with comments (if implemented)

**Acceptance Criteria:** AC-SUP-008, AC-SUP-009, AC-SUP-011, AC-SUP-012, AC-SUP-014

---

### TC-SUP-008: Reject Application - Missing Comments
**Priority:** High  
**Test Objective:** Verify comments are required for rejection.

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Select an application
3. Click "Reject" button
4. Leave comments field empty
5. Click "Confirm Rejection"

**Expected Result:**
- Error message: "Comments are required when rejecting an application"
- Rejection is prevented
- Comments field is highlighted

**Acceptance Criteria:** AC-SUP-009

---

### TC-SUP-009: Approve Already Processed Application
**Priority:** Medium  
**Test Objective:** Verify supervisor cannot approve already processed applications.

**Preconditions:**
- Application is already approved

**Test Steps:**
1. Navigate to "Approved Applications" page
2. Select an approved application
3. Attempt to approve again

**Expected Result:**
- System prevents action
- Error message: "This application has already been processed"

**Acceptance Criteria:** AC-SUP-017

---

### TC-SUP-010: View Only Team Member Applications
**Priority:** High  
**Test Objective:** Verify supervisor can only see applications from their team.

**Preconditions:**
- Supervisor SUP001 manages team with EMP001, EMP002
- EMP003 is not in supervisor's team

**Test Steps:**
1. Log in as SUP001
2. Navigate to "Pending Applications" page
3. Check if EMP003's applications are visible

**Expected Result:**
- Only applications from EMP001 and EMP002 are visible
- EMP003's applications are not displayed

**Acceptance Criteria:** AC-SUP-016

---

### TC-SUP-011: Supervisor Cannot Approve Own Application
**Priority:** High  
**Test Objective:** Verify supervisor cannot approve their own application.

**Preconditions:**
- Supervisor (also an employee) has submitted an application

**Test Steps:**
1. Log in as supervisor
2. Navigate to "Pending Applications" page
3. Attempt to approve own application

**Expected Result:**
- Own application is not visible in pending list OR
- System prevents approval with error message

**Acceptance Criteria:** AC-SUP-015

---

### TC-SUP-012: Bulk Approve Applications (if implemented)
**Priority:** Low  
**Test Objective:** Verify bulk approval functionality (if available).

**Test Steps:**
1. Navigate to "Pending Applications" page
2. Select multiple applications
3. Click "Bulk Approve"
4. Confirm action

**Expected Result:**
- All selected applications are approved
- Status updated for all
- Confirmation message displayed

**Acceptance Criteria:** [If implemented]

---

## Calculation Test Cases

### TC-CALC-001: Unapproved Calculation - Single Day
**Priority:** High  
**Test Objective:** Verify Unapproved T&S calculation for 1 day.

**Test Steps:**
1. Submit application with:
   - Departure Date: 2024-02-01
   - Arrival Date: 2024-02-01
   - Type: Unapproved

**Expected Result:**
- Number of Days: 1
- T&S Amount: $135 (1 × $135)

**Acceptance Criteria:** AC-EMP-006

---

### TC-CALC-002: Unapproved Calculation - Multiple Days
**Priority:** High  
**Test Objective:** Verify Unapproved T&S calculation for multiple days.

**Test Steps:**
1. Submit application with:
   - Departure Date: 2024-02-01
   - Arrival Date: 2024-02-05
   - Type: Unapproved

**Expected Result:**
- Number of Days: 5
- T&S Amount: $675 (5 × $135)

**Acceptance Criteria:** AC-EMP-006

---

### TC-CALC-003: Approved Calculation - Single Day
**Priority:** High  
**Test Objective:** Verify Approved T&S calculation for 1 day.

**Test Steps:**
1. Submit application with:
   - Departure Date: 2024-02-01
   - Arrival Date: 2024-02-01
   - Type: Approved

**Expected Result:**
- Number of Days: 1
- T&S Amount: $300 (1 × $300)

**Acceptance Criteria:** AC-EMP-007

---

### TC-CALC-004: Approved Calculation - Multiple Days
**Priority:** High  
**Test Objective:** Verify Approved T&S calculation for multiple days.

**Test Steps:**
1. Submit application with:
   - Departure Date: 2024-02-01
   - Arrival Date: 2024-02-07
   - Type: Approved

**Expected Result:**
- Number of Days: 7
- T&S Amount: $2,100 (7 × $300)

**Acceptance Criteria:** AC-EMP-007

---

### TC-CALC-005: Day Calculation - Edge Case (Same Day)
**Priority:** Medium  
**Test Objective:** Verify day calculation for same day travel.

**Test Steps:**
1. Submit application with:
   - Departure Date: 2024-02-15
   - Arrival Date: 2024-02-15
   - Type: Unapproved

**Expected Result:**
- Number of Days: 1
- T&S Amount: $135

**Acceptance Criteria:** AC-EMP-006

---

### TC-CALC-006: Day Calculation - Edge Case (Consecutive Days)
**Priority:** Medium  
**Test Objective:** Verify day calculation for consecutive days.

**Test Steps:**
1. Submit application with:
   - Departure Date: 2024-02-01
   - Arrival Date: 2024-02-02
   - Type: Unapproved

**Expected Result:**
- Number of Days: 2
- T&S Amount: $270 (2 × $135)

**Acceptance Criteria:** AC-EMP-006

---

### TC-CALC-007: Day Calculation - Week Long Travel
**Priority:** Medium  
**Test Objective:** Verify calculation for week-long travel.

**Test Steps:**
1. Submit application with:
   - Departure Date: 2024-02-01 (Monday)
   - Arrival Date: 2024-02-07 (Sunday)
   - Type: Approved

**Expected Result:**
- Number of Days: 7
- T&S Amount: $2,100 (7 × $300)

**Acceptance Criteria:** AC-EMP-007

---

### TC-CALC-008: Calculation Display Before Submission
**Priority:** High  
**Test Objective:** Verify calculated amount is displayed before submission.

**Test Steps:**
1. Enter all required fields
2. Select Type: Unapproved
3. Enter dates
4. Before clicking Submit, verify calculated amount is displayed

**Expected Result:**
- Calculated T&S Amount is visible
- Amount updates if dates change
- Amount updates if type changes

**Acceptance Criteria:** AC-EMP-008

---

## System Integration Test Cases

### TC-INT-001: User Authentication
**Priority:** High  
**Test Objective:** Verify user authentication works correctly.

**Test Steps:**
1. Navigate to login page
2. Enter valid credentials
3. Click "Login"

**Expected Result:**
- User is authenticated
- Redirected to appropriate dashboard (Employee or Supervisor)

**Acceptance Criteria:** AC-SYS-005

---

### TC-INT-002: Session Timeout
**Priority:** Medium  
**Test Objective:** Verify session timeout handling.

**Test Steps:**
1. Log in to the system
2. Wait for session timeout (or simulate)
3. Attempt to perform an action

**Expected Result:**
- Session timeout message is displayed
- User is redirected to login page
- Unsaved data is handled appropriately

**Acceptance Criteria:** AC-SYS-006

---

### TC-INT-003: Concurrent Access
**Priority:** Medium  
**Test Objective:** Verify system handles concurrent access.

**Test Steps:**
1. Log in as Supervisor SUP001
2. Log in as Supervisor SUP002 (different browser/device)
3. Both attempt to approve the same application

**Expected Result:**
- System handles concurrent access appropriately
- Only one approval is processed
- Appropriate error message for second attempt

**Acceptance Criteria:** AC-SYS-004

---

### TC-INT-004: Data Integrity - Application Submission
**Priority:** High  
**Test Objective:** Verify data integrity during submission.

**Test Steps:**
1. Submit an application
2. Verify data is saved correctly in database
3. View application to confirm all fields match

**Expected Result:**
- All data is saved correctly
- No data loss or corruption
- Data matches what was entered

**Acceptance Criteria:** AC-SYS-003

---

### TC-INT-005: Error Handling - Network Error
**Priority:** Medium  
**Test Objective:** Verify error handling for network issues.

**Test Steps:**
1. Start submitting an application
2. Simulate network disconnection
3. Attempt to submit

**Expected Result:**
- Appropriate error message is displayed
- User can retry submission
- No data corruption

**Acceptance Criteria:** AC-SYS-002

---

## Test Case Execution Template

| Test Case ID | Test Case Name | Priority | Executed By | Date | Status | Defect ID | Notes |
|--------------|----------------|----------|-------------|------|--------|-----------|-------|
| TC-EMP-001 | Submit T&S Application - Valid Unapproved | High | [Name] | [Date] | Pass/Fail/Blocked | [ID] | [Notes] |

**Status Values:**
- **Pass:** Test case passed
- **Fail:** Test case failed
- **Blocked:** Test case cannot be executed (blocked by defect)
- **Not Executed:** Test case not yet executed

---

**End of Test Cases Document**

