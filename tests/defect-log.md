# 🐞 Defect Log – Book Store App QA Project  
**Team:** PLP TESTERS  
**Last Updated:** 2025-11-17  
**Test Environment:** Chrome 142, Windows 11, Local dev (http://localhost:3000)

---

## 📊 Defect Summary Dashboard

| Metric | Count |
|--------|-------|
| **Total Defects** | 26 |
| **Open** | 26 |
| **In Progress** | 0 |
| **Fixed** | 0 |
| **Verified** | 0 |
| **Closed** | 0 |

### Defects by Severity
- 🔴 **Critical**: 2 (8%)
- 🟠 **Major**: 10 (38%)
- 🟡 **Minor**: 14 (54%)

### Defects by Priority
- 🔥 **High**: 14 (54%)
- ⚠️ **Medium**: 9 (35%)
- 📌 **Low**: 3 (12%)

### Defects by Feature Area
- **Catalog (Filtering/Sorting)**: 8 defects
- **Reviews & Q&A**: 6 defects
- **Admin Functions**: 6 defects
- **Order Management**: 4 defects
- **Coupon System**: 3 defects
- **Cart Validation**: 2 defects

---

## 📋 Severity & Priority Definitions

### Severity Levels
| Level | Definition | Example |
|-------|------------|---------|
| **Critical** | System crash, data loss, security breach | Payment processing completely fails |
| **Major** | Core functionality broken, no workaround | Cannot add items to cart |
| **Minor** | Feature works with issues, workaround exists | Sort order incorrect |
| **Trivial** | Cosmetic issues, typos | Button color slightly off |

### Priority Levels
| Level | Definition | Timeline |
|-------|------------|----------|
| **High** | Must fix before release | Current sprint |
| **Medium** | Should fix soon | Next sprint |
| **Low** | Fix when possible | Backlog |

---

## 🐛 Detailed Defect List

| Defect ID | Summary | Severity | Priority | Status | Found Date | Affected FR(s) | Root Cause |
|-----------|---------|----------|----------|--------|------------|----------------|------------|
| BUG-21 | Admin cannot update order statuses | Major | High | 🔴 Open | 2025-11-10 | FR-M03 | Missing Implementation |
| BUG-22 | Admin cannot moderate reviews | Minor | Medium | 🔴 Open | 2025-11-10 | FR-U02 | Missing Implementation |
| BUG-24 | Refund audit trail missing | Major | High | 🔴 Open | 2025-11-10 | FR-R02 | Missing Implementation |
| BUG-25 | Fulfilled/Delivered states not in order history | Minor | Medium | 🔴 Open | 2025-11-10 | FR-O05 | Incomplete Feature |
| BUG-28 | Genre filter not working | Minor | Medium | 🔴 Open | 2025-11-11 | FR-M01 | Missing Implementation |
| BUG-29 | Price filter not working | Minor | Medium | 🔴 Open | 2025-11-11 | FR-M01 | Missing Implementation |
| BUG-30 | Rating filter not working | Minor | Medium | 🔴 Open | 2025-11-11 | FR-M01 | Missing Implementation |
| BUG-31 | Price sorting not working | Minor | Medium | 🔴 Open | 2025-11-11 | FR-M01 | Missing Implementation |
| BUG-32 | Rating sorting not working | Minor | Medium | 🔴 Open | 2025-11-11 | FR-M01 | Missing Implementation |
| BUG-33 | Popularity sorting not working | Minor | Medium | 🔴 Open | 2025-11-11 | FR-M01 | Missing Implementation |
| BUG-34 | Multi-image gallery with lazy loading missing | Minor | Low | 🔴 Open | 2025-11-11 | FR-M01, FR-X02 | Missing Implementation |
| BUG-35 | Buy Now button not disabled for out-of-stock items | Critical | High | 🔴 Open | 2025-11-12 | FR-M01 | Missing Validation |
| BUG-36 | Cart allows quantity to exceed available stock | Critical | High | 🔴 Open | 2025-11-12 | FR-O01 | Missing Validation |
| BUG-41 | Coupon system not implemented | Major | High | 🔴 Open | 2025-11-12 | FR-O02 | Missing Implementation |
| BUG-42 | Coupon validation not implemented | Major | High | 🔴 Open | 2025-11-12 | FR-O02 | Missing Implementation |
| BUG-43 | Coupon combinability rules not implemented | Major | High | 🔴 Open | 2025-11-12 | FR-O02 | Missing Implementation |
| BUG-49 | Order history page incomplete | Minor | Medium | 🔴 Open | 2025-11-13 | FR-O04 | Incomplete Feature |
| BUG-51 | CSV export functionality missing | Minor | Medium | 🔴 Open | 2025-11-13 | FR-O04 | Missing Implementation |
| BUG-53 | Return window (7-day) validation missing | Minor | Medium | 🔴 Open | 2025-11-13 | FR-R01 | Missing Implementation |
| BUG-54 | Refund processing functionality missing | Major | High | 🔴 Open | 2025-11-13 | FR-R02 | Missing Implementation |
| BUG-55 | Review submission system not implemented | Minor | Medium | 🔴 Open | 2025-11-14 | FR-U01 | Missing Implementation |
| BUG-56 | Duplicate review prevention not implemented | Minor | Low | 🔴 Open | 2025-11-14 | FR-U01 | Missing Implementation |
| BUG-57 | Review content sanitization not implemented | Major | High | 🔴 Open | 2025-11-14 | FR-S01 | Missing Implementation |
| BUG-58 | Review flagging functionality missing | Minor | Low | 🔴 Open | 2025-11-14 | FR-U02 | Missing Implementation |
| BUG-59 | Q&A system with safe markdown not implemented | Minor | Medium | 🔴 Open | 2025-11-14 | FR-U03, FR-S01 | Missing Implementation |
| BUG-61 | Admin catalog CRUD operations missing | Major | High | 🔴 Open | 2025-11-14 | FR-M01 | Missing Implementation |
| BUG-62 | Admin inventory adjustment missing | Major | High | 🔴 Open | 2025-11-14 | FR-M02 | Missing Implementation |

---

## 📝 Detailed Defect Descriptions

### BUG-21: Admin cannot update order statuses
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Login as admin (admin@example.com)
2. Navigate to Orders Dashboard
3. Select an order
4. Attempt to change order status from "Pending" to "Paid"

**Expected Result:**
- Status dropdown should be available
- Status should update when selected
- Change should be reflected in order history
- Audit trail entry should be created

**Actual Result:**
- No status update functionality available
- Orders remain in original status
- Cannot manage order lifecycle

**Impact:** Admin cannot manage order fulfillment process

**Related Test Cases:** T21, T25

---

### BUG-22: Admin cannot moderate reviews
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Login as admin
2. Navigate to Admin Dashboard
3. Look for moderation queue or review management

**Expected Result:**
- Moderation queue should display flagged reviews
- Admin can approve or remove reviews
- Actions should update review status

**Actual Result:**
- No moderation interface available
- Cannot manage user-generated reviews

**Impact:** Cannot moderate inappropriate content

**Related Test Cases:** T22, T58

---

### BUG-24: Refund audit trail missing
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Process a refund (if functionality existed)
2. Check order audit trail
3. Look for refund entry

**Expected Result:**
- Refund action should be logged in audit trail
- Entry should include: amount, date, admin user, reason
- Audit trail should be immutable

**Actual Result:**
- No audit trail system implemented
- Cannot track refund history

**Impact:** No accountability for financial transactions

**Related Test Cases:** T24, T54

---

### BUG-25: Fulfilled/Delivered states not in order history
**Severity:** Major | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Place an order (status: Pending)
2. Complete payment (status: Paid)
3. Update to Fulfilled (if possible)
4. Update to Delivered (if possible)
5. View order history

**Expected Result:**
- Order history should show all lifecycle states
- Timeline should display: Pending → Paid → Fulfilled → Delivered
- Each state should have timestamp

**Actual Result:**
- Only Pending and Paid states visible
- Fulfilled and Delivered states not reflected in UI

**Impact:** Customers cannot track order fulfillment progress

**Related Test Cases:** T25, T52

---

### BUG-28: Genre filter not working
**Severity:** Minor | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to catalog page
2. Look for genre filter options
3. Attempt to filter by genre (e.g., "Fiction", "Mystery")

**Expected Result:**
- Genre filter UI should be available
- Selecting a genre should filter catalog
- Only books matching selected genre(s) should display

**Actual Result:**
- No genre filter functionality available
- Cannot filter books by genre

**Impact:** Users cannot narrow down book selection by category

**Related Test Cases:** T28

---

### BUG-29: Price filter not working
**Severity:** Minor | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to catalog page
2. Look for price range filter
3. Attempt to set price range (e.g., $10-$15)

**Expected Result:**
- Price range filter UI should be available
- Setting min/max price should filter catalog
- Only books within price range should display

**Actual Result:**
- No price filter functionality available
- Cannot filter books by price range

**Impact:** Users cannot find books within their budget

**Related Test Cases:** T29

---

### BUG-30: Rating filter not working
**Severity:** Minor | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to catalog page
2. Look for rating filter options
3. Attempt to filter by minimum rating (e.g., 4+ stars)

**Expected Result:**
- Rating filter UI should be available
- Selecting minimum rating should filter catalog
- Only books meeting rating threshold should display

**Actual Result:**
- No rating filter functionality available
- Cannot filter books by rating

**Impact:** Users cannot find highly-rated books easily

**Related Test Cases:** T30

---

### BUG-31: Price sorting not working
**Severity:** Minor | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to catalog page
2. Look for sort options
3. Attempt to sort by price (low→high or high→low)

**Expected Result:**
- Sort dropdown should include price options
- Selecting "Price: Low to High" should sort ascending
- Selecting "Price: High to Low" should sort descending

**Actual Result:**
- No price sorting functionality available
- Books remain in default order

**Impact:** Users cannot sort by price to find deals or premium items

**Related Test Cases:** T31

---

### BUG-32: Rating sorting not working
**Severity:** Minor | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to catalog page
2. Look for sort options
3. Attempt to sort by rating (highest first)

**Expected Result:**
- Sort dropdown should include rating option
- Selecting "Rating: Highest First" should sort by rating descending
- Highest-rated books should appear first

**Actual Result:**
- No rating sorting functionality available
- Books remain in default order

**Impact:** Users cannot find top-rated books easily

**Related Test Cases:** T32

---

### BUG-33: Popularity sorting not working
**Severity:** Minor | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to catalog page
2. Look for sort options
3. Attempt to sort by popularity (most popular first)

**Expected Result:**
- Sort dropdown should include popularity option
- Selecting "Most Popular" should sort by popularity descending
- Most viewed/purchased books should appear first

**Actual Result:**
- No popularity sorting functionality available
- Books remain in default order

**Impact:** Users cannot discover trending or popular books

**Related Test Cases:** T33

---

### BUG-34: Multi-image gallery with lazy loading missing
**Severity:** Minor | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to book details page
2. Check for multiple product images
3. Inspect image loading behavior
4. Check image alt text

**Expected Result:**
- Multiple images should be displayed (gallery/carousel)
- Images should lazy load (loading="lazy")
- Alt text should include book title and author
- Explicit width/height attributes should be set

**Actual Result:**
- Only single image displayed
- No image gallery functionality
- Alt text may be incomplete

**Impact:** Users cannot view multiple product images; accessibility reduced

**Related Test Cases:** T34, T17

---

### BUG-35: Buy Now button not disabled for out-of-stock items
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to catalog
2. Find a book with stock = 0 (e.g., "Gone Girl", ID=10)
3. Check "Buy Now" button state

**Expected Result:**
- "Buy Now" button should be disabled
- "Out of Stock" badge should be displayed
- User should not be able to add to cart

**Actual Result:**
- "Buy Now" button remains enabled
- User can add out-of-stock items to cart
- No stock indicator displayed

**Impact:** Users can attempt to purchase unavailable items

**Related Test Cases:** T35

---

### BUG-36: Cart allows quantity to exceed available stock
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Add book with limited stock to cart (e.g., "The Catcher in the Rye", stock=3)
2. In cart, increase quantity to 5 (exceeds stock)
3. Click "Update Quantity"

**Expected Result:**
- System should validate against available stock
- Error message: "Only 3 items available"
- Quantity should be capped at stock limit
- Update should be rejected

**Actual Result:**
- No stock validation performed
- Quantity increases to 5
- Subtotal updates incorrectly
- User can order more than available

**Impact:** Risk of overselling and fulfillment issues

**Related Test Cases:** T36

---

### BUG-41, BUG-42, BUG-43: Coupon system not implemented
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Combined Description:**
The entire coupon/discount system is missing from the checkout process.

**Steps to Reproduce:**
1. Add items to cart
2. Proceed to checkout
3. Look for coupon code input field

**Expected Result:**
- Coupon input field should be available
- User can enter coupon code (e.g., "SAVE20")
- System validates coupon:
  - Check expiration date
  - Check minimum basket amount
  - Check combinability rules
- Valid coupon applies discount
- Invalid/expired coupon shows error message

**Actual Result:**
- No coupon input field
- No coupon validation logic
- Cannot apply promotional discounts

**Impact:** Cannot run promotional campaigns; revenue loss

**Related Test Cases:** T41, T42, T43

---

### BUG-49: Order history page incomplete
**Severity:** Major | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Place multiple orders
2. Navigate to "My Orders" or order history page
3. Check displayed orders

**Expected Result:**
- All past orders should be displayed
- Orders sorted by date (newest first)
- Each order shows: ID, date, status, total
- Click order to view details

**Actual Result:**
- Order history page incomplete or missing orders
- Not all orders displayed
- Limited order information

**Impact:** Users cannot track their purchase history

**Related Test Cases:** T49

---

### BUG-51: CSV export functionality missing
**Severity:** Major | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Login as admin
2. Navigate to Orders Dashboard
3. Look for "Export CSV" button
4. Attempt to export orders

**Expected Result:**
- "Export CSV" button should be available
- Clicking generates RFC4180-compliant CSV file
- CSV includes: Order ID, Date, Status, Customer, Items, Totals
- File downloads automatically

**Actual Result:**
- No CSV export functionality available
- Cannot export order data

**Impact:** Admin cannot generate reports for accounting/analysis

**Related Test Cases:** T51

---

### BUG-53: Return window (7-day) validation missing
**Severity:** Major | **Priority:** Medium | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Place and complete an order (status: Delivered)
2. Wait 8 days after delivery
3. Attempt to request return

**Expected Result:**
- System should validate return window
- Returns allowed within 7 days of delivery
- After 7 days, show error: "Return window has expired"
- Display days remaining in return window

**Actual Result:**
- No return request functionality available
- No return window validation

**Impact:** Cannot enforce return policy

**Related Test Cases:** T53

---

### BUG-54: Refund processing functionality missing
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Login as admin
2. Navigate to order with return request
3. Attempt to process refund

**Expected Result:**
- Admin can process full or partial refund
- Refund amount input field available
- Refund reason text area available
- Processing refund updates order status to "Refunded"
- Audit trail entry created

**Actual Result:**
- No refund processing interface available
- Admin cannot process refunds

**Impact:** Cannot handle customer returns and refunds

**Related Test Cases:** T54, T24

---

### BUG-55, BUG-56, BUG-57, BUG-58: Review system not implemented
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Combined Description:**
The entire review and rating system is missing.

**Steps to Reproduce:**
1. Purchase a book
2. Navigate to book details page
3. Look for review section

**Expected Result:**
- Review section should be displayed
- Purchased users can submit reviews (rating + text)
- System validates:
  - User has purchased the book
  - User hasn't already reviewed
  - Content is sanitized (no scripts)
- Reviews display with star rating, date, verified badge
- Users can flag inappropriate reviews

**Actual Result:**
- No review section available
- Cannot submit or view reviews
- No review moderation

**Impact:** No social proof; reduced conversion rates

**Related Test Cases:** T55, T56, T57, T58, T22

---

### BUG-59: Q&A system with safe markdown not implemented
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Navigate to book details page
2. Look for Q&A section
3. Attempt to ask a question

**Expected Result:**
- Q&A section should be displayed
- Users can ask questions about the book
- Users can answer questions
- Markdown formatting supported (safe subset)
- URL validation (only http/https allowed)
- javascript: and data: URLs blocked

**Actual Result:**
- No Q&A section available
- Cannot ask or answer questions

**Impact:** Users cannot get product information from community

**Related Test Cases:** T59

---

### BUG-61: Admin catalog CRUD operations missing
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Login as admin
2. Navigate to Admin Dashboard
3. Look for catalog management
4. Attempt to create/update/delete books

**Expected Result:**
- Admin can create new books (all fields)
- Admin can edit existing books
- Admin can delete books (with confirmation)
- Changes reflect immediately in catalog

**Actual Result:**
- No catalog CRUD interface available
- Admin cannot manage book inventory

**Impact:** Cannot maintain product catalog

**Related Test Cases:** T61

---

### BUG-62: Admin inventory adjustment missing
**Severity:** Major | **Priority:** High | **Status:** 🔴 Open

**Steps to Reproduce:**
1. Login as admin
2. Navigate to inventory management
3. Attempt to adjust stock levels

**Expected Result:**
- Admin can view current stock levels
- Admin can adjust stock quantities
- Low-stock warnings displayed (threshold: 5)
- Stock changes logged in audit trail
- Changes reflect immediately in catalog

**Actual Result:**
- No inventory management interface available
- Admin cannot adjust stock levels
- No low-stock indicators

**Impact:** Cannot manage inventory; risk of stockouts

**Related Test Cases:** T62

---

## 📎 Related Documents

| Document | Purpose | Location |
|----------|---------|----------|
| Test Cases | Detailed test scenarios | [test-cases.md](./test-cases.md) |
| Test Report | Final test results | [Test-Report.md](./Test-Report.md) |
| Comprehensive Report | Executive summary | [Comprehensive-Test-Report.md](./Comprehensive-Test-Report.md) |
| Traceability Matrix | Requirements coverage | [Traceability-matrix.md](./Traceability-matrix.md) |
| Test Plan | Testing strategy | [test-plan.md](./test-plan.md) |

---

## 📝 Notes

- All defects are currently **Open** and unassigned
- Most defects are due to **missing implementations** rather than bugs in existing code
- Priority should be given to **P1 High** defects before release
- Defects BUG-41, BUG-42, BUG-43 are related (coupon system)
- Defects BUG-55, BUG-56, BUG-57, BUG-58 are related (review system)

---

**Document Version:** 2.0  
**Last Updated:** November 17, 2025  
**Updated By:** QA Team
