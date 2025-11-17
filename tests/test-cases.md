# ✅ Test Cases – Book Store App QA Project  
**Team:** PLP Testers  
**Last Updated:** 2025-11-17  
**Test Cycle:** Sprint 6 - Final Testing  
**Application Version:** 1.1.0

---

## 📊 TEST SUMMARY

This document contains all test cases for the Bookstore E-Commerce Web Application. Testing focused on core shopping flows (catalog → cart → checkout → payment → order tracking) and administrative modules. All test cases are mapped to Functional Requirements (FR codes) for full traceability.

### Test Execution Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| **Total Test Cases** | 64 | 100% |
| **Passed** | 38 | 59% |
| **Failed** | 26 | 41% |
| **Not Executed** | 0 | 0% |
| **Blocked** | 0 | 0% |

### Test Results by Category

| Category | Total | Passed | Failed | Pass % |
|----------|-------|--------|--------|--------|
| Catalog & Search | 12 | 6 | 6 | 50% |
| Cart Management | 8 | 6 | 2 | 75% |
| Checkout & Payment | 10 | 7 | 3 | 70% |
| Order Management | 8 | 4 | 4 | 50% |
| Returns & Refunds | 3 | 0 | 3 | 0% |
| Reviews & Q&A | 6 | 0 | 6 | 0% |
| Admin Functions | 8 | 2 | 6 | 25% |
| Accessibility | 3 | 2 | 1 | 67% |
| Performance | 2 | 2 | 0 | 100% |
| Security | 4 | 4 | 0 | 100% |

---

## 🔧 TEST ENVIRONMENT

| Component | Details |
|-----------|---------|
| **Environment** | Local Development (http://localhost:3000) |
| **Browsers** | Chrome 142, Firefox 132, Safari 17, Microsoft Edge 129 |
| **Operating Systems** | Windows 11, macOS 14, Android 13, iOS 17 |
| **Devices** | Desktop (1920x1080), Tablet (iPad Pro), Mobile (iPhone 12 Pro, Samsung Galaxy A34) |
| **Payment Gateway** | Paystack Test Environment |
| **Test Tools** | Chrome DevTools, Cypress 13, React Testing Library, axe-core 4.9, Lighthouse 11 |

---

## 📋 TEST CASES

### Legend
- ✅ **Passed** - Test executed successfully, meets expected result
- ❌ **Failed** - Test did not meet expected result
- ⏸️ **Blocked** - Cannot execute due to dependency
- ⏭️ **Skipped** - Intentionally not executed

---

## 🏠 CATALOG & SEARCH (FR-M01)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T1 | Redirect to Homepage | Verify root URL redirects user to catalog page | Redirects to /catalog | Redirects to /catalog | ✅ Passed | - | FR-M01 |
| T5 | Search by Title | Verify book title search filters catalog | Only matching titles displayed | Only matching titles displayed | ✅ Passed | - | FR-M01 |
| T6 | Search by Author | Verify author name search filters catalog | Only matching authors displayed | Only matching authors displayed | ✅ Passed | - | FR-M01 |
| T16 | Book Details | Verify details page shows title, author, description | All details visible; related section loads | All details visible | ✅ Passed | - | FR-M01 |
| T27 | Catalog Search (Case-Insensitive) | Verify search is case-insensitive and trims whitespace | Matching books displayed; empty query returns full list | Works as expected | ✅ Passed | - | FR-M01 |
| T17 | Lazy Image Loading | Verify images load only in viewport with alt text | Images load on scroll; alt text includes title + author | Images load on scroll with alt text | ✅ Passed | - | FR-X02 |
| T28 | Filter by Genre | Verify selecting a genre filters catalog | Only books of selected genre(s) displayed | No genre filter available | ❌ Failed | BUG-28 | FR-M01 |
| T29 | Filter by Price | Verify price range filter applies correctly | Only books within price range displayed | No price filter available | ❌ Failed | BUG-29 | FR-M01 |
| T30 | Filter by Rating | Verify rating filter applies correctly | Only books meeting minimum rating displayed | No rating filter available | ❌ Failed | BUG-30 | FR-M01 |
| T31 | Sort by Price | Verify sort order low→high & high→low | Books sorted by price in selected order | No price sorting available | ❌ Failed | BUG-31 | FR-M01 |
| T32 | Sort by Rating | Verify sort by highest rating first | Books sorted by rating (highest first) | No rating sorting available | ❌ Failed | BUG-32 | FR-M01 |
| T33 | Sort by Popularity | Verify popularity sort adjusts correctly | Most popular books appear first | No popularity sorting available | ❌ Failed | BUG-33 | FR-M01 |
| T34 | Book Details Images | Verify multiple images load with alt text | All images load lazy, alt includes title+author | Only single image displayed | ❌ Failed | BUG-34 | FR-M01, FR-X02 |
| T35 | Out-of-Stock Restriction | Verify "Buy Now" disabled for stock=0 | "Buy Now" button disabled; "Out of Stock" badge shown | Button remains enabled | ❌ Failed | BUG-35 | FR-M01 |

---

## 🛒 CART MANAGEMENT (FR-O01)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T2 | Add to Cart | Verify clicking "Buy Now" adds book to cart | Book added; cart badge increments | Book added; cart badge increments | ✅ Passed | - | FR-O01 |
| T3 | Update Cart Quantity | Verify changing quantity updates subtotal | Subtotal recalculates accurately | Subtotal recalculates accurately | ✅ Passed | - | FR-O01 |
| T4 | Remove from Cart | Verify removing a book updates subtotal | Book removed; subtotal updates | Book removed; subtotal updates | ✅ Passed | - | FR-O01 |
| T10 | Cart Persistence | Verify cart items persist after reload | Items remain after refresh | Items remain after refresh | ✅ Passed | - | FR-O01 |
| T13 | Subtotal Multi-Items | Verify subtotal updates for multiple books | Correct total displayed | Correct total displayed | ✅ Passed | - | FR-O01 |
| T37 | Cart Persistence (Reload) | Verify cart survives page reload | Cart items remain after refresh | Cart items remain after refresh | ✅ Passed | - | FR-O01 |
| T38 | Subtotal Calculation | Verify subtotal updates for multiple items | Subtotal = sum(price × qty) | Subtotal = sum(price × qty) | ✅ Passed | - | FR-O01 |
| T36 | Cart Quantity Validation | Verify quantity cannot exceed stock | Quantity capped at stock; error shown | No quantity validation | ❌ Failed | BUG-36 | FR-O01 |

---

## 💳 CHECKOUT & PAYMENT (FR-O02, FR-O03)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T7 | Checkout Navigation | Verify checkout wizard loads with summary | Checkout wizard opens correctly | Checkout wizard opens correctly | ✅ Passed | - | FR-O02 |
| T11 | Empty Checkout | Verify checkout blocked when cart is empty | Warning displayed; cannot proceed | Warning displayed; cannot proceed | ✅ Passed | - | FR-O02 |
| T15 | Checkout Wizard Navigation | Verify navigation between steps works | Can move Next/Back smoothly | Can move Next/Back smoothly | ✅ Passed | - | FR-O02 |
| T39 | Shipping Calculation | Verify shipping fee added correctly | Total = subtotal + shipping + tax | Total = subtotal + shipping + tax | ✅ Passed | - | FR-O02 |
| T40 | Tax Calculation | Verify tax computed at 8% of subtotal | Tax = subtotal × 0.08, rounded 2dp | Tax = subtotal × 0.08, rounded 2dp | ✅ Passed | - | FR-O02 |
| T44 | Checkout Wizard Navigation | Verify Next/Back preserves input | User input retained, navigation smooth | User input retained, navigation smooth | ✅ Passed | - | FR-O02 |
| T45 | Checkout Form Validation | Verify required fields enforced | Error messages displayed, aria-live polite | Error messages displayed | ✅ Passed | - | FR-O02 |
| T8 | Paystack Payment | Verify mock Paystack test card completes payment | Payment success screen shown | Payment success screen shown | ✅ Passed | - | FR-O03 |
| T12 | Currency Display | Verify currency matches Paystack currency | NGN displayed consistently | NGN displayed consistently | ✅ Passed | - | FR-O03 |
| T46 | Payment Success | Verify successful Paystack payment updates order | Order status = Paid; reference stored | Order status = Paid; reference stored | ✅ Passed | - | FR-O03 |
| T47 | Payment Cancel | Verify cancel returns user to cart safely | Order remains Pending; retry allowed | Order remains Pending; retry allowed | ✅ Passed | - | FR-O03 |
| T48 | Payment Error | Verify error handling for failed payment | Error banner shown; order remains Pending | Error banner shown; order remains Pending | ✅ Passed | - | FR-O03 |
| T41 | Coupon Valid | Verify valid coupon reduces total | Discount applied; total reduced | No coupon input field available | ❌ Failed | BUG-41 | FR-O02 |
| T42 | Coupon Invalid/Expired | Verify invalid/expired coupon rejected | Error message shown; no discount | No coupon input field available | ❌ Failed | BUG-42 | FR-O02 |
| T43 | Coupon Combinability | Verify non-combinable coupons blocked | Error shown when combining non-combinable | No coupon system available | ❌ Failed | BUG-43 | FR-O02 |

---

## 📦 ORDER MANAGEMENT (FR-O04, FR-O05)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T50 | Order Details | Verify order detail page shows items, totals, shipping | All details visible, dates ISO8601 | All details visible, dates ISO8601 | ✅ Passed | - | FR-O04 |
| T52 | Order Status Transition | Verify status changes Pending→Paid→Fulfilled→Delivered | Statuses updated sequentially | Statuses updated sequentially | ✅ Passed | - | FR-O05 |
| T49 | Order History Display | Verify user sees list of previous orders | All past orders displayed in reverse chronological order | Not all orders displayed | ❌ Failed | BUG-49 | FR-O04 |
| T51 | CSV Export | Verify admin can export orders to CSV | CSV file generated with proper format | No CSV export functionality | ❌ Failed | BUG-51 | FR-O04 |
| T25 | Order Lifecycle | Verify status transitions Pending→Paid→Fulfilled→Delivered | All states reflected in order history | Fulfilled and Delivered not reflected | ❌ Failed | BUG-25 | FR-O05 |
| T21 | Orders Dashboard | Verify admin can update order statuses | Status updates reflected in UI | Cannot update order statuses | ❌ Failed | BUG-21 | FR-M03 |

---

## 🔄 RETURNS & REFUNDS (FR-R01, FR-R02)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T53 | Return Window | Verify returns allowed within 7 days | Return accepted within 7 days; rejected after | No return functionality available | ❌ Failed | BUG-53 | FR-R01 |
| T54 | Refund Processing | Verify admin processes refund & logs audit | Refund processed; audit entry created | No refund processing available | ❌ Failed | BUG-54 | FR-R02 |
| T24 | Refund Audit Trail | Verify refund recorded with audit entry | Audit trail entry with refund details | No audit trail available | ❌ Failed | BUG-24 | FR-R02 |

---

## ⭐ REVIEWS & Q&A (FR-U01, FR-U02, FR-U03)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T55 | Review Submission | Verify only purchasers can submit review | Review form available for purchasers only | No review section available | ❌ Failed | BUG-55 | FR-U01 |
| T56 | Review Duplicate | Verify one review per user/book | Second review blocked with error message | No review system available | ❌ Failed | BUG-56 | FR-U01 |
| T57 | Review Sanitization | Verify scripts stripped from review | Scripts removed; safe content displayed | No review system available | ❌ Failed | BUG-57 | FR-S01 |
| T58 | Review Flagging | Verify user can report review | Review flagged; added to moderation queue | No review system available | ❌ Failed | BUG-58 | FR-U02 |
| T22 | Review Moderation | Verify admin can approve/remove flagged reviews | Moderation actions applied | No moderation interface available | ❌ Failed | BUG-22 | FR-U02 |
| T59 | Q&A Safe Markdown | Verify allowed markdown works; unsafe blocked | Safe markdown rendered; javascript: blocked | No Q&A system available | ❌ Failed | BUG-59 | FR-U03, FR-S01 |

---

## 👨‍💼 ADMIN FUNCTIONS (FR-M01, FR-M02, FR-M03)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T9 | Admin Access | Verify admin can access dashboard | Admin page loads for admin role | Admin page loads for admin role | ✅ Passed | - | FR-M03 |
| T14 | Admin Role Persistence | Verify admin access persists after reload | Admin retains access after reload | Admin retains access after reload | ✅ Passed | - | FR-M03 |
| T23 | Admin Authorization | Verify non-admin blocked from /admin | Unauthorized message displayed | Unauthorized message displayed | ✅ Passed | - | FR-M03 |
| T60 | Admin Unauthorized Access | Verify non-admin blocked from /admin | Unauthorized message displayed | Unauthorized message displayed | ✅ Passed | - | FR-M03 |
| T61 | Admin Catalog CRUD | Verify admin can create/update/delete books | CRUD operations work; changes reflected | No CRUD interface available | ❌ Failed | BUG-61 | FR-M01 |
| T62 | Admin Inventory Adjustment | Verify stock edits trigger low-stock notice | Stock updated; low-stock warning shown | No inventory management available | ❌ Failed | BUG-62 | FR-M02 |

---

## ♿ ACCESSIBILITY (FR-X01)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T64 | Keyboard Navigation | Verify Tab navigation across UI elements | Focus moves correctly through all elements | Focus moves correctly | ✅ Passed | - | FR-X01 |
| T63 | Mark All Read (Known Defect) | Verify mark-all-read updates badge | Badge resets to zero | Badge resets to zero (known defect) | ✅ Passed | - | FR-N02 |

---

## 🚀 PERFORMANCE (FR-X02)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| Performance-LCP | Largest Contentful Paint | Verify LCP ≤ 2.5s | LCP ≤ 2.5s | LCP = 2.1s | ✅ Passed | - | FR-X02 |
| Performance-TTI | Time to Interactive | Verify TTI ≤ 1.0s | TTI ≤ 1.0s | TTI = 0.9s | ✅ Passed | - | FR-X02 |

---

## 🌐 COMPATIBILITY & SECURITY (FR-X03, FR-X04, FR-S01)

| ID | Feature | Objective | Expected Result | Actual Result | Status | Defect ID | FR Link |
|----|---------|-----------|----------------|---------------|--------|-----------|---------|
| T18 | Notifications Badge | Verify unread count updates on new notification | Badge increments properly | Badge increments properly | ✅ Passed | - | FR-N01 |
| T19 | Responsive Layout | Verify layout across mobile, tablet, desktop | All components aligned correctly | All components aligned correctly | ✅ Passed | - | FR-X03 |
| T20 | Compatibility | Verify cross-browser support (Chrome, Firefox, Safari, Edge) | Layout consistent across browsers | Layout consistent across browsers | ✅ Passed | - | FR-X03 |
| T26 | Security Hygiene | Verify user-generated content sanitized | No malicious scripts rendered | No malicious scripts rendered | ✅ Passed | - | FR-X04 |

---

## 📊 TEST METRICS

### Test Execution Timeline
- **Test Planning**: Nov 1-4, 2025
- **Test Case Development**: Nov 5-7, 2025
- **Test Execution**: Nov 8-14, 2025
- **Defect Reporting**: Nov 8-14, 2025
- **Final Report**: Nov 15-17, 2025

### Defect Distribution
- **Total Defects Found**: 26
- **Critical**: 0
- **Major**: 18 (69%)
- **Minor**: 8 (31%)

### Test Coverage
- **Requirements Coverage**: 100% (51/51 requirements tested)
- **Code Coverage**: ~85% (estimated)
- **Feature Coverage**: 100% (all features tested)

---

## 📎 RELATED DOCUMENTS

| Document | Purpose | Location |
|----------|---------|----------|
| Test Plan | Overall testing strategy | [test-plan.md](./test-plan.md) |
| Defect Log | Detailed defect information | [defect-log.md](./defect-log.md) |
| Test Report | Final test results | [Test-Report.md](./Test-Report.md) |
| Comprehensive Report | Executive summary | [Comprehensive-Test-Report.md](./Comprehensive-Test-Report.md) |
| Traceability Matrix | Requirements coverage | [Traceability-matrix.md](./Traceability-matrix.md) |

---

## 📝 NOTES

### Test Data Used
- **Books**: 12 sample books with varying prices, genres, and stock levels
- **Users**: test@example.com (customer), admin@example.com (admin)
- **Payment**: Paystack test cards (success/failure scenarios)
- **Coupons**: SAVE20, WELCOME10, EXPIRED2024 (for testing when implemented)

### Known Issues
- T63: Mark All Read badge reset is a known defect (accepted)
- T25: Shows "Passed" status but has partial failure (Fulfilled/Delivered states missing)

### Test Environment Notes
- All tests executed on local development environment
- Payment gateway in test mode (no real transactions)
- Test data reset before each test cycle

---

**Document Version:** 2.0  
**Last Updated:** November 17, 2025  
**Updated By:** QA Team  
**Next Review:** Post-Release (November 24, 2025)
