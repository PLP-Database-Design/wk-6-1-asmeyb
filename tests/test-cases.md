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
|T21|Orders Dashboard|Verify admin can update order statuses|Status updates reflected in UI|||FR-M03|
|T22|Review Moderation|Verify admin can approve/remove flagged reviews|Moderation actions applied|||FR-U02|
|T23|Admin Authorization|Verify non-admin blocked from /admin|Unauthorized message displayed|||FR-M03|
|T24|Refund Audit Trail|Verify refund recorded with audit entry|Refund appears; audit entry logged|||FR-R02|
|T25|Order Lifecycle|Verify status transitions Pending→Paid→Fulfilled→Delivered|Each step reflected in order history|Works as expected|Passed|FR-O05|
|T26|Security Hygiene|Verify user-generated content sanitized||||FR-X04|


---
|Metric	|Count|
|--------|-----|
|Total Test Cases|	26|
|Passed|	20|
|Failed| |
|Not Executed	|6|
Pass Percentage|	77%|










