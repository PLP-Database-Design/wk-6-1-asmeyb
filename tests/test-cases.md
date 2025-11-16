# ✅ Test Cases – Book Store App QA Project  
**Team:** :**PLP Testers**;`  
**Last updated:– 2025-11-13
## TEST SUMMARY
This report summarizes the functional and integration testing of the Bookstore E-Commerce Web App.
The focus was on core shopping flows (catalog → cart → checkout → payment → order tracking) and administrative modules.
Testing covered  paths aligned with the defined Functional Requirement (FR) codes.

---
## TEST ENVIROMENT
Environment	Staging: 
Browser(s)	:Chrome , Firefox , Safari,Microsoft Edge .

OS:	Windows 10 / Android 

Payment Gateway:	Paystack

Tools Used:	 Chrome DevTools (Performance)

---


## TEST CASES

| ID | Feature | Objective | Expected Result | Actual Result | Status | Risk Link |
|----|---------|-----------|----------------|---------------|--------|-----------| 
|T1|	Redirect to homepage|	Verify root URL redirects user to catalog page	|Redirects to /catalog|	Works as expected|	Passed	|FR-M01|
|T2|Add to Cart|Verify that clicking “Buy Now” adds book to cart|Book added; cart badge increments|Works as expected|Passed|FR-001|
|T3	|Update Cart Quantity|	Verify that changing quantity updates subtotal	|Subtotal recalculates accurately|	Works as expected|	Passed	|FR-001|
|T4|Remove from Cart|Verify that removing a book updates subtotal|Book removed; subtotal updates|Works as expected|Passed|FR-001|
|T5	|Search by Title|	Verify book title search filters catalog|	Only matching titles displayed|	Works as expected|	Passed|	FR-M01|
|T6	|Search by Author	|Verify author name search filters catalog|	Does not filter catalog by authors 	|work as expected|	passed|FR-M01|
|T7	|Checkout Navigation|	Verify checkout wizard loads with summary|	Checkout wizard opens correctly|	Works as expected	|Passed	|FR-O02|
|T8	|Paystack Payment|	Verify mock Paystack test card completes payment|	Payment success screen shown|	Works as expected|	Passed|FR-O03	|
|T9	|Admin Access|	Verify admin can access dashboard|	Admin page loads for admin role	|Works as expected|	Passed	|FR-M03|
|T10|Cart Persistence|	Verify cart items persist after reload|	Items remain after refresh|	Works as expected|	Passed|FR-O01	|
|T11|Empty Checkout	|Verify checkout blocked when cart is empty|	Warning displayed; no proceed|	Works as expected|	Passed|FR-O02	|
|T12|Currency Display	|Verify currency matches Paystack currency|	NGN displayed consistently	|Works as expected|	Passed|	FR-O03|
|T13|Subtotal Multi-Items	|Verify subtotal updates for multiple books|	Correct total displayed	|Works as expected	|Passed|FR-O01	|
|T14|Admin Role Persistence	|Verify admin access persists after reload|	Admin retains access|	Works as expected|	Passed	|FR-M03|
|T15|Checkout Wizard Navigation|	Verify navigation between steps works|	Can move Next/Back smoothly	|Works as expected|	Passed|FR-O02|
|T16|Book Details|Verify details page shows title, author|All details visible; related section loads|Works as expected|Passed|FR-M01|
|T17|Lazy Image Loading|Verify images load only in viewport with alt text|Images load on scroll; alt text includes title + author|worked as expected| passed|FR-X02|
|T18|Notifications Badge|Verify unread count updates on new notification|Badge increments properly|Works as expected|Passed|FR-N01|
|T19|Responsive Layout|Verify layout across mobile, tablet, desktop|All components aligned correctly|Works as expected|Passed|FR-X03|
|T20|Compatibility|Verify cross-browser support (Chrome, Firefox, Safari, Edge)|Layout consistent across browsers|Works as expected|Passed|FR-X03|
|T21|Orders Dashboard|Verify admin can update order statuses|Status updates reflected in UI|Does not work as expected|failed|FR-M03|
|T22|Review Moderation|Verify admin can approve/remove flagged reviews|Moderation actions applied|Does not work as expected|Failed|FR-U02|
|T23|Admin Authorization|Verify non-admin blocked from /admin|Unauthorized message displayed|Work as expected|Passed|FR-M03|
|T24|Refund Audit Trail|Verify refund recorded with audit entry|Audit trail not availabla|Does not work as expected|failed|FR-R02|
|T25|Order Lifecycle|Verify status transitions Pending→Paid→Fulfilled→Delivered|fulfilled and delivered not reflected in order history|Does not work as expected|Passed|FR-O05|
|T26|Security Hygiene|Verify user-generated content sanitized||||FR-X04|
| T27 | Catalog Search               | Verify search is case-insensitive and trims whitespace | Matching books displayed; empty query returns full list | Works as expected | Passed | FR-M01         |
| T28 | Filter by Genre              | Verify selecting a genre filters catalog               | Does                     | Works as expected | Passed | FR-M01         |
| T29 | Filter by Price              | Verify price band filter applies correctly             | Only books within range displayed                       |  Does not work as expected | Failed| FR-M01         |
| T30 | Filter by Rating             | Verify rating filter applies correctly                 | Only books with selected rating shown                   |  Does not work as expected | Failed | FR-M01         |
| T31 | Sort by Price                | Verify sort order low→high & high→low                  | Books ordered correctly                                 |  Does not work as expected | Failed | FR-M01         |
| T32 | Sort by Rating               | Verify sort by highest rating first                    | Highest rated books appear first                        |  Does not work as expected | Failed | FR-M01         |
| T33 | Sort by Popularity           | Verify popularity sort adjusts correctly               | Most popular books first                                | Does not work as expected |Failed | FR-M01         |
| T34 | Book Details Images          | Verify multiple images load with alt text              | All images load lazy, alt includes title+author         |   Does not work as expected|  Failed| FR-M01, FR-X02 |
| T35 | Out-of-Stock Restriction     | Verify “Buy Now” disabled for stock=0                  |    No restriction on the stock           | Does not work as expected | Failed | FR-M01         |
| T36 | Cart Quantity Validation     | Verify quantity cannot exceed stock                    | No quantity validation        | Does not works as expected | Failed | FR-O01         |
| T37 | Cart Persistence             | Verify cart survives page reload                       | Cart items remain after refresh                         | Works as expected | Passed | FR-O01         |
| T38 | Subtotal Calculation         | Verify subtotal updates for multiple items             | Subtotal = sum(price × qty)                             | Works as expected | Passed | FR-O01         |
| T39 | Shipping Calculation         | Verify shipping fee added correctly                    | Total = subtotal + shipping + tax                       | Works as expected | Passed | FR-O02         |
| T40 | Tax Calculation              | Verify tax computed at 8% of subtotal                  | Tax = subtotal × 0.08, rounded 2dp                      | Works as expected | Passed | FR-O02         |
| T41 | Coupon Valid                 | Verify valid coupon reduces total                      | Coupon does not show                                 | Does not work as expected | Failed | FR-O02         |
| T42 | Coupon Invalid/Expired       | Verify invalid/expired coupon rejected                 | Coupon doe not show                |Does not work as expected | Failed| FR-O02         |
| T43 | Coupon Combinability         | Verify non-combinable coupons blocked                  | Coupon not available                          |Does not work as expected | Failed | FR-O02         |
| T44 | Checkout Wizard Navigation   | Verify Next/Back preserves input                       | User input retained, navigation smooth                  | Works as expected | Passed | FR-O02         |
| T45 | Checkout Form Validation     | Verify required fields enforced                        | Error messages displayed, aria-live polite              | Works as expected | Passed | FR-O02         |
| T46 | Payment Success              | Verify successful Paystack payment updates order       | Order status = Paid; reference stored                   | Works as expected | Passed | FR-O03         |
| T47 | Payment Cancel               | Verify cancel returns user to cart safely              | Order remains Pending; retry allowed                    | Works as expected | Passed | FR-O03         |
| T48 | Payment Error                | Verify error handling for failed payment               | Error banner shown; order remains Pending               | Works as expected | Passed | FR-O03         |
| T49 | Order History Display        | Verify user sees list of previous orders               | All past orders not displayed                     | Does not work as expected | Failed | FR-O04         |
| T50 | Order Details                | Verify order detail page shows items, totals, shipping | All details visible, dates ISO8601                      | Works as expected | Passed | FR-O04         |
| T51 | CSV Export                   | Verify admin can export orders to CSV                  | Can not export CSV file           |Does  not work as expected | Failed | FR-O04         |
| T52 | Order Status Transition      | Verify status changes Pending→Paid→Fulfilled→Delivered | Statuses updated sequentially                           | Works as expected | Passed | FR-O05         |
| T53 | Return Window                | Verify returns allowed within 7 days                   | No return policy            | Does not work as expected | Failed| FR-R01         |
| T54 | Refund Processing            | Verify admin processes refund & logs audit             | Admin can not process refunds                    | Does not work as expected | Failed | FR-R02         |
| T55 | Review Submission            | Verify only purchasers can submit review               | No review section              |   Does not work as expected | Failed | FR-U01         |
| T56 | Review Duplicate             | Verify one review per user/book                        | No review section                           | Does not work as expected | Failed | FR-U01         |
| T57 | Review Sanitization          | Verify scripts stripped from review                    | No review section              | Does not work as expected | Failed | FR-S01         |
| T58 | Review Flagging              | Verify user can report review                          | No review section             |Does not work as expected | Failed | FR-U02         |
| T59 | Q&A Safe Markdown            | Verify allowed markdown works; unsafe blocked          | No Q&A safe Markdown         | Does not work as expected | Failed | FR-U03, FR-S01 |
| T60 | Admin Unauthorized Access    | Verify non-admin blocked from /admin                   | Unauthorized message displayed                          | Works as expected | Passed | FR-M03         |
| T61 | Admin Catalog CRUD           | Verify admin can create/update/delete books            |   Admin cannot create/update/delete books       |Does not work as expected  | Failed | FR-M01       |
| T62 | Admin Inventory Adjustment   | Verify stock edits trigger low-stock notice            |Admin cannot verify or edit stocks                        |Does not work as expected  | Failed | FR-M02 |
| T63 | Mark All Read (Defect)       | Verify mark-all-read updates badge                     | Badge resets to zero (known defect)                     | Failed            | FR-N02 |
| T64 | Keyboard Navigation          | Verify Tab navigation across UI elements               | Focus moves correctly                                   | Works as expected | FR-X01 |                


---
|Metric	|Count|
|--------|-----|
|Total Test Cases|	64|
|Passed|	20|
|Failed| |
|Not Executed	|6|
Pass Percentage|	77%|










