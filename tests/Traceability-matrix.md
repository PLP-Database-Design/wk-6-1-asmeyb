# 🔗 Requirements Traceability Matrix  
**Team:** PLP Testers  
**Version:** 2.0  
**Date:** November 17, 2025  
**Application Version:** 1.1.0

---

## 📊 EXECUTIVE SUMMARY

This Requirements Traceability Matrix (RTM) provides bidirectional traceability between Functional Requirements (FRs) and Test Cases (TCs). It ensures 100% requirements coverage and identifies gaps in testing or implementation.

### Key Metrics

| Metric | Count | Percentage |
|--------|-------|------------|
| **Total Functional Requirements** | 21 | 100% |
| **Requirements Tested** | 21 | 100% |
| **Requirements Passed** | 5 | 24% |
| **Requirements Failed** | 16 | 76% |
| **Test Cases Executed** | 64 | 100% |
| **Test Cases Passed** | 38 | 59% |
| **Test Cases Failed** | 26 | 41% |

---

## 🔗 REQUIREMENTS TO TEST CASES MAPPING

| FR Code | Requirement Description | Linked Test Cases | Total Tests | Passed | Failed | Status | Priority |
|---------|------------------------|-------------------|-------------|--------|--------|--------|----------|
| **FR-M01** | Catalog: browse, search, filter, sort, details, images, stock display | T1, T5, T6, T16, T27, T28, T29, T30, T31, T32, T33, T34, T35, T61 | 14 | 6 | 8 | ❌ Failed | High |
| **FR-M02** | Inventory: adjustments, low-stock warnings | T62 | 1 | 0 | 1 | ❌ Failed | High |
| **FR-M03** | Admin: authorization, dashboard, order management | T9, T14, T21, T23, T60 | 5 | 4 | 1 | ❌ Failed | High |
| **FR-O01** | Cart: add, remove, update, stock validation, persistence | T2, T3, T4, T10, T13, T36, T37, T38 | 8 | 7 | 1 | ❌ Failed | High |
| **FR-O02** | Checkout: wizard, validation, coupons, shipping, tax | T7, T11, T15, T39, T40, T41, T42, T43, T44, T45 | 10 | 7 | 3 | ❌ Failed | High |
| **FR-O03** | Payment: Paystack integration, currency, success/cancel/error | T8, T12, T46, T47, T48 | 5 | 5 | 0 | ✅ Passed | High |
| **FR-O04** | Orders: history display, details, CSV export | T49, T50, T51 | 3 | 1 | 2 | ❌ Failed | Medium |
| **FR-O05** | Orders: lifecycle transitions (Pending→Paid→Fulfilled→Delivered) | T25, T52 | 2 | 1 | 1 | ❌ Failed | High |
| **FR-R01** | Returns: 7-day window validation | T53 | 1 | 0 | 1 | ❌ Failed | Medium |
| **FR-R02** | Refunds: processing, audit trail | T24, T54 | 2 | 0 | 2 | ❌ Failed | High |
| **FR-U01** | Reviews: purchaser validation, duplicate prevention | T55, T56 | 2 | 0 | 2 | ❌ Failed | Medium |
| **FR-U02** | Reviews: moderation queue, flagging | T22, T58 | 2 | 0 | 2 | ❌ Failed | Medium |
| **FR-U03** | Q&A: safe markdown, URL validation | T59 | 1 | 0 | 1 | ❌ Failed | Medium |
| **FR-N01** | Notifications: unread count, history | T18 | 1 | 1 | 0 | ✅ Passed | Low |
| **FR-N02** | Notifications: mark-all-read | T63 | 1 | 1 | 0 | ✅ Passed | Low |
| **FR-X01** | Accessibility: WCAG 2.1 AA, keyboard navigation | T64 | 1 | 1 | 0 | ✅ Passed | High |
| **FR-X02** | Performance: LCP ≤ 2.5s, TTI ≤ 1.0s, lazy loading | T17, T34, Performance-LCP, Performance-TTI | 4 | 3 | 1 | ❌ Failed | High |
| **FR-X03** | Compatibility: cross-browser, responsive | T19, T20 | 2 | 2 | 0 | ✅ Passed | High |
| **FR-X04** | Security: sanitize UGC, block scripts | T26 | 1 | 1 | 0 | ✅ Passed | High |
| **FR-S01** | Security: sanitization rules, block javascript: | T57, T59 | 2 | 0 | 2 | ❌ Failed | High |

---

## 🔄 REVERSE TRACEABILITY: TEST CASES TO REQUIREMENTS

### Catalog & Search Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T1 | Redirect to Homepage | FR-M01 | ✅ Passed |
| T5 | Search by Title | FR-M01 | ✅ Passed |
| T6 | Search by Author | FR-M01 | ✅ Passed |
| T16 | Book Details | FR-M01 | ✅ Passed |
| T17 | Lazy Image Loading | FR-X02 | ✅ Passed |
| T27 | Catalog Search (Case-Insensitive) | FR-M01 | ✅ Passed |
| T28 | Filter by Genre | FR-M01 | ❌ Failed |
| T29 | Filter by Price | FR-M01 | ❌ Failed |
| T30 | Filter by Rating | FR-M01 | ❌ Failed |
| T31 | Sort by Price | FR-M01 | ❌ Failed |
| T32 | Sort by Rating | FR-M01 | ❌ Failed |
| T33 | Sort by Popularity | FR-M01 | ❌ Failed |
| T34 | Book Details Images | FR-M01, FR-X02 | ❌ Failed |
| T35 | Out-of-Stock Restriction | FR-M01 | ❌ Failed |

### Cart Management Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T2 | Add to Cart | FR-O01 | ✅ Passed |
| T3 | Update Cart Quantity | FR-O01 | ✅ Passed |
| T4 | Remove from Cart | FR-O01 | ✅ Passed |
| T10 | Cart Persistence | FR-O01 | ✅ Passed |
| T13 | Subtotal Multi-Items | FR-O01 | ✅ Passed |
| T36 | Cart Quantity Validation | FR-O01 | ❌ Failed |
| T37 | Cart Persistence (Reload) | FR-O01 | ✅ Passed |
| T38 | Subtotal Calculation | FR-O01 | ✅ Passed |

### Checkout & Payment Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T7 | Checkout Navigation | FR-O02 | ✅ Passed |
| T8 | Paystack Payment | FR-O03 | ✅ Passed |
| T11 | Empty Checkout | FR-O02 | ✅ Passed |
| T12 | Currency Display | FR-O03 | ✅ Passed |
| T15 | Checkout Wizard Navigation | FR-O02 | ✅ Passed |
| T39 | Shipping Calculation | FR-O02 | ✅ Passed |
| T40 | Tax Calculation | FR-O02 | ✅ Passed |
| T41 | Coupon Valid | FR-O02 | ❌ Failed |
| T42 | Coupon Invalid/Expired | FR-O02 | ❌ Failed |
| T43 | Coupon Combinability | FR-O02 | ❌ Failed |
| T44 | Checkout Wizard Navigation | FR-O02 | ✅ Passed |
| T45 | Checkout Form Validation | FR-O02 | ✅ Passed |
| T46 | Payment Success | FR-O03 | ✅ Passed |
| T47 | Payment Cancel | FR-O03 | ✅ Passed |
| T48 | Payment Error | FR-O03 | ✅ Passed |

### Order Management Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T21 | Orders Dashboard | FR-M03 | ❌ Failed |
| T25 | Order Lifecycle | FR-O05 | ❌ Failed |
| T49 | Order History Display | FR-O04 | ❌ Failed |
| T50 | Order Details | FR-O04 | ✅ Passed |
| T51 | CSV Export | FR-O04 | ❌ Failed |
| T52 | Order Status Transition | FR-O05 | ✅ Passed |

### Returns & Refunds Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T24 | Refund Audit Trail | FR-R02 | ❌ Failed |
| T53 | Return Window | FR-R01 | ❌ Failed |
| T54 | Refund Processing | FR-R02 | ❌ Failed |

### Reviews & Q&A Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T22 | Review Moderation | FR-U02 | ❌ Failed |
| T55 | Review Submission | FR-U01 | ❌ Failed |
| T56 | Review Duplicate | FR-U01 | ❌ Failed |
| T57 | Review Sanitization | FR-S01 | ❌ Failed |
| T58 | Review Flagging | FR-U02 | ❌ Failed |
| T59 | Q&A Safe Markdown | FR-U03, FR-S01 | ❌ Failed |

### Admin Functions Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T9 | Admin Access | FR-M03 | ✅ Passed |
| T14 | Admin Role Persistence | FR-M03 | ✅ Passed |
| T23 | Admin Authorization | FR-M03 | ✅ Passed |
| T60 | Admin Unauthorized Access | FR-M03 | ✅ Passed |
| T61 | Admin Catalog CRUD | FR-M01 | ❌ Failed |
| T62 | Admin Inventory Adjustment | FR-M02 | ❌ Failed |

### Non-Functional Tests
| Test ID | Test Name | Linked FRs | Status |
|---------|-----------|------------|--------|
| T18 | Notifications Badge | FR-N01 | ✅ Passed |
| T19 | Responsive Layout | FR-X03 | ✅ Passed |
| T20 | Compatibility | FR-X03 | ✅ Passed |
| T26 | Security Hygiene | FR-X04 | ✅ Passed |
| T63 | Mark All Read | FR-N02 | ✅ Passed |
| T64 | Keyboard Navigation | FR-X01 | ✅ Passed |
| Performance-LCP | Largest Contentful Paint | FR-X02 | ✅ Passed |
| Performance-TTI | Time to Interactive | FR-X02 | ✅ Passed |

---

## 📈 COVERAGE ANALYSIS

### Requirements Coverage by Priority

| Priority | Total FRs | Tested | Passed | Failed | Coverage % | Pass % |
|----------|-----------|--------|--------|--------|------------|--------|
| **High** | 13 | 13 | 3 | 10 | 100% | 23% |
| **Medium** | 6 | 6 | 0 | 6 | 100% | 0% |
| **Low** | 2 | 2 | 2 | 0 | 100% | 100% |
| **TOTAL** | **21** | **21** | **5** | **16** | **100%** | **24%** |

### Test Coverage by Feature Area

| Feature Area | Requirements | Test Cases | Coverage % |
|--------------|--------------|------------|------------|
| Catalog Management | 1 | 14 | 100% |
| Cart Operations | 1 | 8 | 100% |
| Checkout & Payment | 2 | 15 | 100% |
| Order Management | 2 | 6 | 100% |
| Returns & Refunds | 2 | 3 | 100% |
| Reviews & Q&A | 3 | 6 | 100% |
| Admin Functions | 3 | 6 | 100% |
| Notifications | 2 | 2 | 100% |
| Accessibility | 1 | 1 | 100% |
| Performance | 1 | 4 | 100% |
| Compatibility | 1 | 2 | 100% |
| Security | 2 | 3 | 100% |

---

## 🔍 GAP ANALYSIS & RECOMMENDATIONS

### Critical Gaps (High Priority)

| Gap Area | Related FRs | Impact | Failed Tests | Recommendation |
|----------|-------------|--------|--------------|----------------|
| **Catalog Filtering/Sorting** | FR-M01 | High | T28, T29, T30, T31, T32, T33 | **P1**: Implement FilterService with genre, price, rating filters and sorting logic |
| **Stock Validation** | FR-O01 | High | T36 | **P1**: Implement stock validation in cart operations to prevent overselling |
| **Coupon System** | FR-O02 | High | T41, T42, T43 | **P1**: Implement CouponService with validation rules (expiry, min basket, combinability) |
| **Admin Order Management** | FR-M03 | High | T21 | **P1**: Implement order status update functionality for admins |
| **Refund Processing** | FR-R02 | High | T24, T54 | **P2**: Implement refund processing with audit trail logging |

### Medium Priority Gaps

| Gap Area | Related FRs | Impact | Failed Tests | Recommendation |
|----------|-------------|--------|--------------|----------------|
| **Order History** | FR-O04 | Medium | T49, T51 | **P2**: Complete order history display and CSV export functionality |
| **Order Lifecycle** | FR-O05 | Medium | T25 | **P2**: Implement Fulfilled and Delivered status transitions |
| **Returns Window** | FR-R01 | Medium | T53 | **P3**: Implement 7-day return window validation |
| **Review System** | FR-U01, FR-U02 | Medium | T22, T55, T56, T57, T58 | **P3**: Implement review submission, validation, and moderation |
| **Q&A System** | FR-U03 | Medium | T59 | **P3**: Implement Q&A with safe markdown support |
| **Admin Catalog CRUD** | FR-M01 | Medium | T61 | **P2**: Implement admin catalog management interface |
| **Inventory Management** | FR-M02 | Medium | T62 | **P2**: Implement inventory adjustment with low-stock warnings |

### Low Priority Gaps

| Gap Area | Related FRs | Impact | Failed Tests | Recommendation |
|----------|-------------|--------|--------------|----------------|
| **Multi-Image Gallery** | FR-X02 | Low | T34 | **P4**: Implement image gallery with lazy loading |

---

## 📊 REQUIREMENTS STATUS SUMMARY

### By Implementation Status

| Status | Count | Percentage | Requirements |
|--------|-------|------------|--------------|
| **Fully Implemented** | 5 | 24% | FR-O03, FR-N01, FR-N02, FR-X01, FR-X03, FR-X04 |
| **Partially Implemented** | 6 | 29% | FR-M01, FR-M03, FR-O01, FR-O02, FR-O04, FR-O05, FR-X02 |
| **Not Implemented** | 10 | 48% | FR-M02, FR-R01, FR-R02, FR-U01, FR-U02, FR-U03, FR-S01 |

### By Business Impact

| Impact Level | Requirements | Status | Action Required |
|--------------|--------------|--------|-----------------|
| **Critical** | FR-O01, FR-O02, FR-O03 | 1 Passed, 2 Failed | Fix stock validation and coupon system |
| **High** | FR-M01, FR-M03, FR-O05, FR-R02 | 0 Passed, 4 Failed | Implement filtering, admin features |
| **Medium** | FR-O04, FR-R01, FR-U01, FR-U02, FR-U03, FR-M02 | 0 Passed, 6 Failed | Plan for next release |
| **Low** | FR-N01, FR-N02, FR-X01, FR-X02, FR-X03, FR-X04 | 5 Passed, 1 Failed | Maintain current quality |

---

## 🎯 IMPLEMENTATION ROADMAP

### Phase 1: Critical Fixes (Week 1-2)
**Goal**: Make application production-ready

1. ✅ Implement stock validation (FR-O01) - BUG-36, BUG-35
2. ✅ Implement coupon system (FR-O02) - BUG-41, BUG-42, BUG-43
3. ✅ Implement admin order management (FR-M03) - BUG-21
4. ✅ Fix order lifecycle display (FR-O05) - BUG-25

**Success Criteria**: All P1 defects resolved, core commerce flow working

### Phase 2: High Priority Features (Week 3-4)
**Goal**: Enhance user experience

1. ✅ Implement catalog filtering (FR-M01) - BUG-28, BUG-29, BUG-30
2. ✅ Implement catalog sorting (FR-M01) - BUG-31, BUG-32, BUG-33
3. ✅ Implement admin catalog CRUD (FR-M01) - BUG-61
4. ✅ Implement inventory management (FR-M02) - BUG-62
5. ✅ Complete order history (FR-O04) - BUG-49, BUG-51

**Success Criteria**: Product discovery improved, admin can manage catalog

### Phase 3: Medium Priority Features (Week 5-6)
**Goal**: Add social proof and customer service

1. ✅ Implement review system (FR-U01, FR-U02) - BUG-55, BUG-56, BUG-57, BUG-58, BUG-22
2. ✅ Implement Q&A system (FR-U03) - BUG-59
3. ✅ Implement returns and refunds (FR-R01, FR-R02) - BUG-53, BUG-54, BUG-24

**Success Criteria**: Users can review products, request returns

### Phase 4: Polish & Optimization (Week 7-8)
**Goal**: Enhance visual experience

1. ✅ Implement multi-image gallery (FR-X02) - BUG-34
2. ✅ Performance optimizations
3. ✅ UI/UX improvements
4. ✅ Additional testing

**Success Criteria**: Professional product presentation, optimal performance

---

## 📎 RELATED DOCUMENTS

| Document | Purpose | Location |
|----------|---------|----------|
| Test Plan | Testing strategy and approach | [test-plan.md](./test-plan.md) |
| Test Cases | Detailed test scenarios | [test-cases.md](./test-cases.md) |
| Defect Log | Bug tracking and details | [defect-log.md](./defect-log.md) |
| Test Report | Summary of test results | [Test-Report.md](./Test-Report.md) |
| Comprehensive Report | Executive summary | [Comprehensive-Test-Report.md](./Comprehensive-Test-Report.md) |

---

## 📝 NOTES

### Coverage Methodology
- **100% Requirements Coverage**: All 21 functional requirements have associated test cases
- **Bidirectional Traceability**: Each requirement maps to tests, each test maps to requirements
- **Gap Identification**: Failed tests indicate missing or incomplete implementations

### Test Execution Notes
- All 64 test cases executed successfully (no blocked or skipped tests)
- 38 tests passed (59%), 26 tests failed (41%)
- Failures primarily due to missing implementations, not bugs in existing code

### Quality Assessment
- **Strengths**: Excellent performance, security, and compatibility
- **Weaknesses**: Many features not yet implemented
- **Risk**: 16 failed requirements represent significant functionality gaps

---

## ✅ SIGN-OFF

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| QA Lead | Asmamaw Yismaw | AY | Nov 17, 2025 |
| Test Engineer | Whitney Shisia | WS | Nov 17, 2025 |
| Test Engineer | Jostina Mwamburi | JM | Nov 17, 2025 |

---

## 📋 DOCUMENT REVISION HISTORY

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | Nov 16, 2025 | Asmamaw Yismaw | Initial version |
| 2.0 | Nov 17, 2025 | Asmamaw Yismaw | Updated with corrected data, added reverse traceability, gap analysis |

---

**END OF TRACEABILITY MATRIX**

**Document Status:** Final  
**Next Review:** Post-Release (November 24, 2025)
