# Test Data and Test Environment Setup Guide
## Travelling and Subsistence (T&S) Allowance Application System

**Document Version:** 1.0  
**Date:** November 5, 2025  
**Document by:** Tinashe Ephraim Nyoni

---

## Table of Contents.

1. [Test Environment Setup](#test-environment-setup)
2. [Test User Accounts](#test-user-accounts)
3. [Test Data Scenarios](#test-data-scenarios)
4. [Test Data Preparation](#test-data-preparation)
5. [Database Setup](#database-setup)
6. [Environment Access](#environment-access)

---

## 1. Test Environment Setup

### 1.1 Environment Details

**Test Environment URL:** [To be provided by Development Team]

**Environment Type:** UAT/Staging Environment

**Database:** Test Database (separate from production)

**Browser Requirements:**
- Google Chrome (latest version)
- Mozilla Firefox (latest version)
- Microsoft Edge (latest version)

### 1.2 Prerequisites

- Internet connection
- Valid user credentials (provided separately)
- Access to test environment URL
- Basic understanding of system functionality

---

## 2. Test User Accounts

### 2.1 Employee Test Accounts

| Employee ID | Password | Role | Team | Supervisor | Status |
|-------------|----------|------|------|------------|--------|
| EMP001 | [Password] | Employee | Team A | SUP001 | Active |
| EMP002 | [Password] | Employee | Team A | SUP001 | Active |
| EMP003 | [Password] | Employee | Team B | SUP002 | Active |
| EMP004 | [Password] | Employee | Team B | SUP002 | Active |
| EMP005 | [Password] | Employee | Team C | SUP001 | Active |

**Note:** Passwords will be provided separately via secure channel.

### 2.2 Supervisor Test Accounts

| Supervisor ID | Password | Role | Team Managed | Employees | Status |
|---------------|----------|------|--------------|-----------|--------|
| SUP001 | [Password] | Supervisor | Team A, Team C | EMP001, EMP002, EMP005 | Active |
| SUP002 | [Password] | Supervisor | Team B | EMP003, EMP004 | Active |

**Note:** SUP001 manages multiple teams to test supervisor access control.

### 2.3 Test Account Setup Instructions

1. Development team will create test accounts in the system
2. Credentials will be shared via secure channel
3. Test accounts should have appropriate permissions
4. Test accounts should be isolated from production data

---

## 3. Test Data Scenarios

### 3.1 Pre-existing Test Data

The following test data should be pre-populated in the test environment:

#### 3.1.1 Pending Applications (for Supervisor Review)

| Application ID | Employee ID | Departure Date | Arrival Date | Type | Amount | Status |
|----------------|-------------|----------------|--------------|------|--------|--------|
| APP001 | EMP001 | 2025-11-15 | 2025-11-17 | Unapproved | $405 | Pending |
| APP002 | EMP002 | 2025-11-20 | 2025-11-20 | Approved | $300 | Pending |
| APP003 | EMP003 | 2025-11-25 | 2025-11-28 | Unapproved | $540 | Pending |
| APP004 | EMP001 | 2025-12-01 | 2025-12-01 | Approved | $300 | Pending |
| APP005 | EMP002 | 2025-12-05 | 2025-12-07 | Unapproved | $405 | Pending |

#### 3.1.2 Approved Applications

| Application ID | Employee ID | Departure Date | Arrival Date | Type | Amount | Status | Approved By | Approved Date |
|----------------|-------------|----------------|--------------|------|--------|--------|-------------|---------------|
| APP006 | EMP001 | 2025-10-01 | 2025-10-03 | Unapproved | $405 | Approved | SUP001 | 2025-10-01 |
| APP007 | EMP002 | 2025-10-10 | 2025-10-10 | Approved | $300 | Approved | SUP001 | 2025-10-10 |
| APP008 | EMP003 | 2025-10-15 | 2025-10-18 | Unapproved | $540 | Approved | SUP002 | 2025-10-15 |

#### 3.1.3 Rejected Applications

| Application ID | Employee ID | Departure Date | Arrival Date | Type | Amount | Status | Rejected By | Rejected Date | Comments |
|----------------|-------------|----------------|--------------|------|--------|--------|-------------|---------------|----------|
| APP009 | EMP001 | 2025-10-05 | 2025-10-09 | Approved | $1500 | Rejected | SUP001 | 2025-10-05 | Travel dates not approved |
| APP010 | EMP002 | 2025-10-12 | 2025-10-14 | Unapproved | $405 | Rejected | SUP001 | 2025-10-12 | Insufficient justification |

---

## 4. Test Data Preparation

### 4.1 Test Scenarios for Manual Testing

#### Scenario 1: Single Day Travel - Unapproved
- **Departure Date:** 2025-11-18
- **Departure Time:** 08:00
- **Arrival Date:** 2025-11-18
- **Arrival Time:** 20:00
- **Departure City:** New York
- **Arrival City:** Boston
- **Type:** Unapproved
- **Expected Amount:** $135 (1 day × $135)

#### Scenario 2: Single Day Travel - Approved
- **Departure Date:** 2025-11-19
- **Departure Time:** 06:00
- **Arrival Date:** 2025-11-19
- **Arrival Time:** 22:00
- **Departure City:** Los Angeles
- **Arrival City:** San Francisco
- **Type:** Approved
- **Expected Amount:** $300 (1 day × $300)

#### Scenario 3: Multi-Day Travel - Unapproved
- **Departure Date:** 2025-11-22
- **Departure Time:** 09:00
- **Arrival Date:** 2025-11-25
- **Arrival Time:** 17:00
- **Departure City:** Chicago
- **Arrival City:** Miami
- **Type:** Unapproved
- **Expected Amount:** $540 (4 days × $135)

#### Scenario 4: Multi-Day Travel - Approved
- **Departure Date:** 2025-11-27
- **Departure Time:** 07:00
- **Arrival Date:** 2025-12-02
- **Arrival Time:** 19:00
- **Departure City:** Seattle
- **Arrival City:** New York
- **Type:** Approved
- **Expected Amount:** $1,800 (6 days × $300)

#### Scenario 5: Weekend Travel
- **Departure Date:** 2025-11-28 (Friday)
- **Departure Time:** 18:00
- **Arrival Date:** 2025-11-30 (Sunday)
- **Arrival Time:** 12:00
- **Departure City:** Dallas
- **Arrival City:** Houston
- **Type:** Unapproved
- **Expected Amount:** $405 (3 days × $135)

### 4.2 Edge Cases for Testing

#### Edge Case 1: Same Day, Different Times
- Same departure and arrival dates
- Arrival time before departure time (should fail validation)

#### Edge Case 2: Maximum Travel Period
- Test with maximum allowed travel period (if defined)

#### Edge Case 3: Duplicate Application
- Attempt to submit duplicate application for same travel period

#### Edge Case 4: Boundary Dates
- Test with dates at month/year boundaries
- Test with leap year dates

---

## 5. Database Setup

### 5.1 Database Schema Requirements

The test database should include the following tables:

1. **users** - User accounts (employees and supervisors)
2. **ts_applications** - T&S applications
3. **ts_approvals** - Approval/rejection records
4. **notifications** - Notification records (if implemented)

### 5.2 Test Data SQL Scripts

The development team should provide SQL scripts to:
- Create test users
- Insert sample applications
- Set up relationships between users and supervisors
- Populate test data for various scenarios

### 5.3 Data Reset Procedure

Before each UAT session:
1. Reset test database to initial state
2. Re-run test data setup scripts
3. Verify all test accounts are active
4. Verify pre-existing applications are in correct state

---

## 6. Environment Access

### 6.1 Access Information

**Test Environment URL:** [To be provided]

**Access Method:** Web Browser

**Authentication:** Username/Password

### 6.2 Getting Access

1. Contact UAT Coordinator: [Name and Email]
2. Request test account credentials
3. Credentials will be provided via secure channel
4. Test accounts are active from UAT start date

### 6.3 Environment Issues

If you encounter any issues accessing the test environment:
1. Check internet connection
2. Verify URL is correct
3. Clear browser cache and cookies
4. Try different browser
5. Contact Development Team: [Contact Information]

---

## 7. Test Data Maintenance

### 7.1 Data Refresh

- Test data will be refreshed daily during UAT period
- Contact Development Team if data needs to be reset

### 7.2 Adding New Test Data

- UAT panelists can create new test data during testing
- Use test accounts provided (EMP001-EMP005, SUP001-SUP002)
- Follow test scenarios provided

### 7.3 Data Cleanup

- Test data created during UAT will be cleaned up after completion
- Pre-existing test data will be preserved for reference

---

## 8. Test Environment Checklist

Before starting UAT, verify:

- ✅ Test environment URL is accessible
- ✅ Test accounts are active and credentials work
- ✅ Pre-existing test data is present
- ✅ Browser compatibility confirmed
- ✅ All required features are available
- ✅ No production data is visible
- ✅ Environment is stable and responsive

---

## 9. Contact Information

**UAT Coordinator:** [Name and Email]  
**Development Team Lead:** [Name and Email]  
**Database Administrator:** [Name and Email]  
**System Administrator:** [Name and Email]

---

## 10. Appendix: Sample Test Data Templates

### 10.1 Application Submission Template

```
Employee ID: [EMP001-EMP005]
Departure Date: YYYY-MM-DD
Departure Time: HH:MM (24-hour format)
Departure City: [City Name]
Arrival Date: YYYY-MM-DD
Arrival Time: HH:MM (24-hour format)
Arrival City: [City Name]
Type of T&S Allowance: [Unapproved/Approved]
Expected T&S Amount: $[Calculated Amount]
```

### 10.2 Approval/Rejection Template

```
Application ID: [APP001-APP010]
Decision: [Approve/Reject]
Comments: [If rejected, provide reason]
```

---

**End of Test Data Guide**

