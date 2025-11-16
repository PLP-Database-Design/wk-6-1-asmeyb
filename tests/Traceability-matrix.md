# 🔗 Requirements Traceability Matrix  
**Team:** PLP Testers  
**Version:** 1.0  
**Date:** 2025-11-16  

| FR Code | Requirement Description | Linked Test Cases (Tx) | Severity | Impact | Priority | Overall Status | Failing Test Cases |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **FR-O01** | Cart operations: add/remove/update with stock enforcement & persistence | T2, T3, T4, T10, T13, T36, T37, T38 | High | High | High | **Failed** | T36 (No quantity validation) |
| **FR-O02** | Checkout wizard navigation, validation, and coupons | T7, T11, T15, T39, T40, T41, T42, T43, T44, T45 | High | High | High | **Failed** | T41, T42, T43 (Coupon functionality missing) |
| **FR-O03** | Payments via Paystack: currency, success/cancel/error | T8, T12, T46, T47, T48 | High | High | High | **Passed** | None |
| **FR-O04** | Order history; CSV export | T49, T50, T51 | Medium | Medium | Medium | **Failed** | T49 (History missing), T51 (CSV export failed) |
| **FR-O05** | Order lifecycle transitions Pending→Delivered | T25, T52 | High | High | High | **Failed** | T25 (Transitions not reflected in history) |
| **FR-R01** | Returns — 7-day window validation | T53 | Medium | Medium | Medium | **Failed** | T53 (No return policy) |
| **FR-R02** | Refund simulation; audit entries | T24, T54 | High | High | High | **Failed** | T24 (Audit trail missing), T54 (Admin cannot process refunds) |
| **FR-M01** | Catalog CRUD: search, filter, sort, details, images | T1, T5, T6, T16, T27, T28, T29, T30, T31, T32, T33, T34, T35, T61 | **High** | **High** | **High** | **Failed** | T28-T35 (Filters/Sorts failed), T61 (Admin CRUD failed) |
| **FR-M02** | Inventory adjustments & low-stock warnings | T62 | High | High | High | **Failed** | T62 (Admin cannot verify/edit stocks) |
| **FR-M03** | Admin console authorization and dashboard | T9, T14, T21, T23, T60 | Medium | High | High | **Failed** | T21 (Orders dashboard status update failed) |
| **FR-N01** | Notifications — unread count, history | T18 | Low | Low | Low | **Passed** | None |
| **FR-N02** | Mark-all-read batch update (intentional defect) | T63 | Low | Low | Low | **Passed** | None (Defect confirmed working) |
| **FR-R03** | Admin approval for returns | (Implied by FR-R02) | Medium | Medium | Medium | **Failed** | T54 (Admin cannot process refunds) |
| **FR-U01** | Reviews — purchasers only; one review per title | T55, T56 | Medium | Low | Medium | **Failed** | T55, T56 (Review section missing) |
| **FR-U02** | Moderation queue for flagged reviews | T22, T58 | Medium | Medium | Medium | **Failed** | T22 (Moderation failed), T58 (Flagging failed) |
| **FR-U03** | Q&A — safe markdown whitelist | T59 | Medium | Low | Medium | **Failed** | T59 (Q&A section missing) |
| **FR-X01** | Accessibility (WCAG 2.1 AA) | T64 | Medium | High | High | **Passed** | None |
| **FR-X02** | Performance (LCP/TTI); lazy loading | T17, T34 | High | High | High | **Failed** | T34 (Multiple images load failed) |
| **FR-X03** | Compatibility — latest 2 browsers | T19, T20 | Medium | High | High | **Passed** | None |
| **FR-X04** | Security hygiene — sanitize UGC; block scripts | T26 | High | High | High | **Passed** | None |
| **FR-S01** | Sanitization rules — block javascript: | T57, T59 | High | High | High | **Failed** | T57, T59 (Related functionality missing) |

# 📈 Requirements Traceability Summary 

## Summary of Requirement Status

This section reflects the current health of the functional requirements based on the executed test cases (Tx) and their failure rates.

| Summary Metric | Count |
| :--- | :--- |
| **Total Functional Requirements** | 22 |
| **Requirements with Failures** | 17 |
| **Requirements Fully Passed** | 4 (FR-O03, FR-N01, FR-X03, FR-X04) |
| **Top Failing Area** | **FR-M01 (Catalog: Filters/Sorts/CRUD)** with 11 failed test cases. |

---

## Summary Statistics

The total scope includes 21 explicit FR Codes plus the implied major feature area of Catalog Filtering/Sorting/Detail (FR-M01), for a conceptual total of 22 requirements in scope.

| Metric | Count | Percentage |
| :--- | :--- | :--- |
| **Total FRs in Scope** | 22 | N/A |
| **Covered (✔ + 🟡)** | 22 | **100%** |
| **Passed (✔)** | 4 | **18%** |
| **Known Bugs / Seeded (🟡)** | 1 | **5%** |
| **Not Executed (❌)** | 0 | 0% |

---

## 🔍 Gap Analysis & Recommendations

Based on the failures reported, the priority for the next development sprint must be fixing the core commerce and catalog deficiencies.

| Area / Defect | Related FR Code(s) | Impact / Example Failure | High-Level Recommendation |
| :--- | :--- | :--- | :--- |
| **Catalog Functionality Missing** | **FR-M01** | High impact. Filters/Sorts (T28-T33) are missing; Admin CRUD (T61) failed. | **P1 Priority:** Implement core **Filter and Sort logic**. Enable Admin CRUD for data management. |
| **Cart/Stock Validation** | **FR-O01** | High impact. Quantity validation (T36) against stock limits is missing. | **P1 Priority:** Enforce **quantity validation** and implement pessimistic lock logic for stock safety. |
| **Coupon/Promotions Failure** | **FR-O02** | High impact. Coupon application and validation (T41, T42, T43) failed/is missing. | **P1 Priority:** Implement **coupon logic** and enforce validation rules (min basket, combinability) before next deployment. |
| **Order/Refund Audit Failure** | **FR-R02, FR-M03** | High impact. Refund processing (T54) and Audit Trail (T24) failed. | **P2 Priority:** Fix the **refund processing flow** and ensure all actions are logged with a persistent audit entry. |
| **UGC/Reviews Missing** | **FR-U01, FR-U03** | Medium impact. Review/Q&A sections (T55, T59) failed/are missing. | **P3 Priority:** Develop the base UI components for **Reviews and Q&A**, ensuring proper purchaser checks are implemented. |

---

## 📎 Appendix

| Document | Location |
| :--- | :--- |
| Full Defect Log | `tests/defect-log.md` |
| Full Test Case Sheet | `tests/test-cases.md` |
