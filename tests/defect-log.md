# 🐞 Defect Log – Book Store App QA Project  
**Team:** PLP TESTERS  
**Current as of:** 2025-11-16  
**Environment:** Local dev, Chrome 130, macOS 14, commit `bfb73f8`

| Defect ID | Summary | Severity | Priority | Environment | Affected FR(s) | Steps to Reproduce | Expected Result | Actual Result |
|-----------|---------|----------|----------|-------------|----------------|--------------------|-----------------|----------------|
| BUG-21 | Admin cannot update order statuses | Major | High | Chrome/Windows 10 | FR-M03 | 1. Login as admin <br> 2. Go to Orders Dashboard <br> 3. Change order status | Status should update and reflect | Status does not change |
| BUG-22 | Admin cannot moderate reviews | Major | High | Chrome/Windows 10 | FR-U02 | 1. Login as admin <br> 2. Navigate to Reviews <br> 3. Approve/remove flagged review | Review state should update | No moderation update |
| BUG-24 | Refund audit trail missing | Major | High | Chrome/Windows 10 | FR-R02 | 1. Process refund <br> 2. Check audit logs | Refund audit entry recorded | No audit trail available |
| BUG-25 | Fulfilled/Delivered not reflected in order history | Major | Medium | Chrome/Windows 10 | FR-O05 | 1. Update order through all lifecycle states <br> 2. View order history | All states should appear | Fulfilled/Delivered missing |
| BUG-28 | Genre filter not working | Minor | Medium | Chrome/Windows 10 | FR-M01 | 1. Open catalog <br> 2. Select a genre | Catalog filtered by genre | No change applied |
| BUG-29 | Price filter not working | Minor | Medium | Chrome/Windows 10 | FR-M01 | 1. Open catalog <br> 2. Apply price filter | Catalog filtered by price | No price filtering |
| BUG-30 | Rating filter not working | Minor | Medium | Chrome/Windows 10 | FR-M01 | 1. Open catalog <br> 2. Apply rating filter | List sorted by rating | No rating filtering |
| BUG-31 | Price sorting not working | Minor | Medium | Chrome/Windows 10 | FR-M01 | 1. Sort by price <br> 2. Select low→high or high→low | Sorted correctly | No sorting applied |
| BUG-32 | Rating sorting not working | Minor | Medium | Chrome/Windows 10 | FR-M01 | 1. Sort by rating | Items sorted by rating | Sorting not working |
| BUG-33 | Popularity sorting not working | Minor | Medium | Chrome/Windows 10 | FR-M01 | 1. Sort by popularity | Popular books appear first | Sorting fails |
| BUG-34 | Multi-image alt text inaccurate | Minor | Medium | Chrome/Windows 10 | FR-M01, FR-X02 | 1. Open book details <br> 2. Inspect all images | All images load with correct alt | Alt text/loading incorrect |
| BUG-35 | Buy Now not disabled for out-of-stock items | Major | High | Chrome/Windows 10 | FR-M01 | 1. View out-of-stock product | Buy Now disabled | Button enabled |
| BUG-36 | Quantity exceeds stock | Major | High | Chrome/Windows 10 | FR-O01 | 1. Add item to cart <br> 2. Increase qty beyond stock | Qty capped at stock | Qty allowed above stock |
| BUG-41 | Valid coupon not applying | Major | High | Chrome/Windows 10 | FR-O02 | 1. Go to checkout <br> 2. Apply valid coupon | Discount applies | No coupon section |
| BUG-42 | Invalid/Expired coupon not rejected | Major | High | Chrome/Windows 10 | FR-O02 | 1. Apply invalid coupon | Error shown | No coupon section |
| BUG-43 | Coupon combinability not enforced | Major | High | Chrome/Windows 10 | FR-O02 | 1. Apply multiple coupons | Non-combinable blocked | Coupon system missing |
| BUG-49 | Order history incomplete | Major | Medium | Chrome/Windows 10 | FR-O04 | 1. View Order History | All past orders displayed | Not all orders shown |
| BUG-51 | CSV export not working | Major | Medium | Chrome/Windows 10 | FR-O04 | 1. Go to Admin Orders <br> 2. Click Export CSV | CSV file generated | No CSV exported |
| BUG-53 | Return window not enforced | Major | Medium | Chrome/Windows 10 | FR-R01 | 1. Attempt return <7 days | Return permitted | No return logic |
| BUG-54 | Refund processing not available | Major | High | Chrome/Windows 10 | FR-R02 | 1. Process refund | Refund + audit recorded | Admin cannot process refund |
| BUG-55 | Review submission unavailable | Major | High | Chrome/Windows 10 | FR-U01 | 1. Purchase book <br> 2. Attempt review | Review form appears | No review section |
| BUG-56 | Duplicate review check missing | Major | Medium | Chrome/Windows 10 | FR-U01 | 1. Submit review twice | Second review blocked | No review system |
| BUG-57 | Review sanitization missing | Major | High | Chrome/Windows 10 | FR-S01 | 1. Submit review with `<script>` | Script stripped | No review feature |
| BUG-58 | Review flagging missing | Major | Medium | Chrome/Windows 10 | FR-U02 | 1. Try flagging a review | Review flagged | No review module |
| BUG-59 | Q&A safe markdown missing | Major | High | Chrome/Windows 10 | FR-U03, FR-S01 | 1. Create Q&A post with markdown | Safe markdown rendered | No Q&A feature |
| BUG-61 | Admin cannot perform Catalog CRUD | Major | High | Chrome/Windows 10 | FR-M01 | 1. Login admin <br> 2. Try create/update/delete | CRUD operations work | Admin CRUD missing |
| BUG-62 | Inventory adjustment not available | Major | High | Chrome/Windows 10 | FR-M02 | 1. Admin edits stock levels | Low-stock indicator updates | No stock controls |
