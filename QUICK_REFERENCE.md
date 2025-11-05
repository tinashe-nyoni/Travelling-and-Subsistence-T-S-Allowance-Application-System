# Quick Reference Guide
## T&S Allowance Application System - UAT

**Document by:** Tinashe Ephraim Nyoni  
**Quick navigation for common UAT tasks**

---

## 📋 T&S Calculation Quick Reference

### Unapproved T&S Allowance.
- **Breakfast:** $15/day
- **Lunch:** $20/day
- **Dinner:** $25/day
- **Accommodation:** $75/day
- **Total per day:** $135

**Formula:** `Days × $135`

**Example:**
- Travel: 2025-11-15 to 2025-11-17 (3 days)
- Amount: 3 × $135 = **$405**

### Approved T&S Allowance
- **Total per day:** $300

**Formula:** `Days × $300`

**Example:**
- Travel: 2025-11-15 to 2025-11-17 (3 days)
- Amount: 3 × $300 = **$900**

### Days Calculation
- Count all days from Departure Date to Arrival Date (inclusive)
- Same day = 1 day
- Example: Nov 15 to Nov 17 = 3 days

---

## 🔑 Test Account Quick Reference

| Role | ID | Team | Supervisor |
|------|----|----|-----------|
| Employee | EMP001 | Team A | SUP001 |
| Employee | EMP002 | Team A | SUP001 |
| Employee | EMP003 | Team B | SUP002 |
| Employee | EMP004 | Team B | SUP002 |
| Employee | EMP005 | Team C | SUP001 |
| Supervisor | SUP001 | Manages Team A, C | - |
| Supervisor | SUP002 | Manages Team B | - |

---

## 📝 Test Case Priority Quick Reference

- **High Priority:** Must pass for UAT sign-off
- **Medium Priority:** Should pass for UAT sign-off
- **Low Priority:** Nice to have, can be deferred

---

## 🐛 Defect Priority Quick Reference

| Priority | Response Time | Examples |
|----------|---------------|----------|
| **P1 - Critical** | 24 hours | System crash, calculation errors, data loss |
| **P2 - High** | 48 hours | Major functionality broken, workflow blocked |
| **P3 - Medium** | 5 days | Minor issues, workaround available |
| **P4 - Low** | Next release | Cosmetic, minor improvements |

---

## ✅ Acceptance Criteria Status Symbols

- ⬜ **Not Started**
- 🟡 **In Progress**
- ✅ **Passed**
- ❌ **Failed**
- ⚠️ **Blocked**
- ⏸️ **Deferred**

---

## 📊 Test Case Execution Status

- **Pass:** Test case passed
- **Fail:** Test case failed
- **Blocked:** Cannot execute (blocked by defect)
- **Not Executed:** Not yet executed

---

## 🔗 Document Quick Links

| Need | Document |
|------|----------|
| Overview of UAT | [UAT_PLAN.md](UAT_PLAN.md) |
| Test scenarios | [TEST_CASES.md](TEST_CASES.md) |
| Track acceptance criteria | [ACCEPTANCE_CRITERIA_MATRIX.md](ACCEPTANCE_CRITERIA_MATRIX.md) |
| Test data setup | [TEST_DATA_GUIDE.md](TEST_DATA_GUIDE.md) |
| How to execute tests | [UAT_EXECUTION_GUIDE.md](UAT_EXECUTION_GUIDE.md) |
| Main navigation | [README.md](README.md) |

---

## 🚨 Common Issues & Solutions

### Issue: Cannot access test environment
**Solution:** Contact Development Team or UAT Coordinator

### Issue: Test case is unclear
**Solution:** Ask UAT Coordinator for clarification

### Issue: Test data missing
**Solution:** Check TEST_DATA_GUIDE.md or contact Development Team

### Issue: Defect already reported
**Solution:** Check defect tracking system, add notes if new information

### Issue: Calculation seems wrong
**Solution:** Verify using formulas in this guide, check test case expected results

---

## 📞 Quick Contact

- **UAT Coordinator:** [Contact Info]
- **Development Team:** [Contact Info]
- **Project Manager:** [Contact Info]

---

## 🎯 Critical Test Cases (Must Pass)

### Employee Functions
- TC-EMP-001: Submit valid Unapproved application
- TC-EMP-002: Submit valid Approved application
- TC-EMP-003: Mandatory field validation
- TC-EMP-005: Date validation
- TC-EMP-009: View pending status
- TC-EMP-010: View approved status
- TC-EMP-011: View rejected status

### Supervisor Functions
- TC-SUP-001: View pending applications
- TC-SUP-006: Approve application
- TC-SUP-007: Reject application with comments
- TC-SUP-010: Team-based access control

### Calculations
- TC-CALC-001: Unapproved single day
- TC-CALC-002: Unapproved multiple days
- TC-CALC-003: Approved single day
- TC-CALC-004: Approved multiple days

---

## 📅 UAT Schedule Quick View

| Day | Activity |
|-----|----------|
| 1 | Smoke Testing |
| 2-4 | Functional Testing |
| 5-7 | Defect Resolution |
| 8-9 | Regression Testing |
| 10 | Sign-off |

---

**End of Quick Reference Guide**

