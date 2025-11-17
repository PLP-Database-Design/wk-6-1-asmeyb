# Requirements Document

## Introduction

This specification addresses the critical missing features and defects identified during QA testing of the Book Store App. The testing revealed 26 failed test cases across multiple functional areas, with the highest priority issues in catalog filtering/sorting, cart validation, coupon management, order management, and admin functionality. This feature set will bring the application to full compliance with the documented functional requirements (FR-O01 through FR-S03).

## Glossary

- **Catalog System**: The book browsing and discovery interface that displays available books
- **Cart System**: The shopping cart that manages items selected for purchase
- **Checkout System**: The multi-step wizard for completing purchases (Shipping → Review → Payment → Confirmation)
- **Order System**: The order tracking and history management system
- **Admin Console**: The administrative interface for managing catalog, inventory, orders, and moderation
- **Coupon Engine**: The promotional discount system with validation rules
- **Review System**: The user-generated rating and review functionality
- **Audit Trail**: The immutable log of administrative actions and state changes
- **Stock Limit**: The maximum available quantity for a book
- **Minor Units**: The smallest currency denomination (cents) for payment processing

## Requirements

### Requirement 1: Catalog Filtering and Sorting

**User Story:** As a user, I want to filter and sort books by multiple criteria, so that I can quickly find books that match my preferences

#### Acceptance Criteria

1. WHEN a user selects a genre filter, THE Catalog System SHALL display only books matching that genre
2. WHEN a user selects a price range filter, THE Catalog System SHALL display only books within that price range
3. WHEN a user selects a rating filter, THE Catalog System SHALL display only books meeting the minimum rating threshold
4. WHEN a user selects price sorting, THE Catalog System SHALL reorder books by price in ascending or descending order
5. WHEN a user selects rating sorting, THE Catalog System SHALL reorder books by rating in descending order
6. WHEN a user selects popularity sorting, THE Catalog System SHALL reorder books by popularity metric in descending order
7. WHEN multiple filters are active, THE Catalog System SHALL combine filters using AND logic
8. WHEN no books match the active filters, THE Catalog System SHALL display a message indicating which filter eliminated results

### Requirement 2: Cart Quantity Validation

**User Story:** As a user, I want the system to prevent me from adding more items than available in stock, so that I don't attempt to purchase unavailable inventory

#### Acceptance Criteria

1. WHEN a user attempts to increase cart quantity beyond stock limit, THE Cart System SHALL reject the change and display an error message
2. WHEN a user views a book with zero stock, THE Catalog System SHALL disable the "Buy Now" button
3. WHEN stock data is updated, THE Cart System SHALL validate existing cart quantities against new stock limits
4. THE Cart System SHALL persist quantity validation state across page reloads

### Requirement 3: Coupon Management

**User Story:** As a user, I want to apply discount coupons during checkout, so that I can reduce my purchase total

#### Acceptance Criteria

1. WHEN a user applies a valid coupon code, THE Checkout System SHALL reduce the order total by the coupon discount amount
2. WHEN a user applies an expired coupon, THE Checkout System SHALL reject the coupon and display an expiration message
3. WHEN a user applies a coupon below minimum basket threshold, THE Checkout System SHALL reject the coupon and display the minimum requirement
4. WHEN a user attempts to combine non-combinable coupons, THE Checkout System SHALL reject the second coupon and display a combinability error
5. THE Checkout System SHALL recalculate totals immediately when a valid coupon is applied
6. WHEN a coupon is removed, THE Checkout System SHALL restore the original total

### Requirement 4: Order History and CSV Export

**User Story:** As a user, I want to view my complete order history and export it as CSV, so that I can track my purchases and maintain records

#### Acceptance Criteria

1. THE Order System SHALL display all orders for the current user in reverse chronological order
2. WHEN a user views order details, THE Order System SHALL display all order items, totals, shipping information, and status timeline
3. WHEN an admin exports orders to CSV, THE Order System SHALL generate an RFC4180-compliant CSV file with UTF-8 encoding
4. THE Order System SHALL format dates in ISO8601 format in the CSV export
5. THE Order System SHALL use dot notation for decimal values in CSV to ensure Excel compatibility

### Requirement 5: Order Lifecycle Management

**User Story:** As an admin, I want to update order statuses through their lifecycle, so that customers can track their order progress

#### Acceptance Criteria

1. WHEN an admin changes order status, THE Order System SHALL update the status and record the change in the audit trail
2. THE Order System SHALL enforce valid status transitions: Pending → Paid → Fulfilled → Delivered
3. THE Order System SHALL allow Cancelled and Refunded statuses from any state with audit justification
4. WHEN order status changes, THE Order System SHALL update the status timeline visible to the user
5. THE Order System SHALL persist all status changes across page reloads

### Requirement 6: Returns and Refunds

**User Story:** As a user, I want to request returns within the return window, so that I can return unwanted purchases

#### Acceptance Criteria

1. WHEN a user requests a return within 7 days of delivery, THE Order System SHALL accept the return request
2. WHEN a user requests a return after 7 days of delivery, THE Order System SHALL reject the return request with a clear message
3. WHEN an admin processes a refund, THE Order System SHALL update order status to Refunded and record the action in the audit trail
4. THE Order System SHALL support full and partial refund amounts
5. THE Order System SHALL display refund information in the order details view

### Requirement 7: Review System

**User Story:** As a purchaser, I want to rate and review books I've bought, so that I can share my experience with other shoppers

#### Acceptance Criteria

1. WHEN a user who purchased a book submits a review, THE Review System SHALL accept and display the review
2. WHEN a user who has not purchased a book attempts to review, THE Review System SHALL reject the review with a clear message
3. WHEN a user attempts to submit a second review for the same book, THE Review System SHALL reject the duplicate with a clear message
4. WHEN a user submits a review containing script tags, THE Review System SHALL sanitize the content and strip malicious code
5. WHEN a user flags a review, THE Review System SHALL add the review to the admin moderation queue
6. THE Review System SHALL allow users to edit or delete their own reviews

### Requirement 8: Admin Catalog Management

**User Story:** As an admin, I want to create, update, and delete books in the catalog, so that I can maintain accurate inventory

#### Acceptance Criteria

1. WHEN an admin creates a new book, THE Admin Console SHALL add the book to the catalog with all required fields
2. WHEN an admin updates book details, THE Admin Console SHALL save changes and reflect them immediately in the catalog
3. WHEN an admin deletes a book, THE Admin Console SHALL remove it from the catalog and handle existing cart references
4. THE Admin Console SHALL validate all required fields before saving book data
5. THE Admin Console SHALL restrict catalog management to users with admin role

### Requirement 9: Inventory Management

**User Story:** As an admin, I want to adjust stock levels and receive low-stock warnings, so that I can maintain adequate inventory

#### Acceptance Criteria

1. WHEN an admin adjusts stock quantity, THE Admin Console SHALL update the stock level immediately
2. WHEN stock falls below the low-stock threshold, THE Admin Console SHALL display a warning indicator
3. THE Admin Console SHALL prevent negative stock values
4. THE Admin Console SHALL log all inventory adjustments in the audit trail
5. WHEN stock reaches zero, THE Catalog System SHALL automatically disable the "Buy Now" button

### Requirement 10: Q&A System

**User Story:** As a user, I want to ask and answer questions about books using safe markdown, so that I can get product information from the community

#### Acceptance Criteria

1. WHEN a user posts a question with safe markdown, THE Q&A System SHALL render the formatted content
2. WHEN a user includes a link with javascript: scheme, THE Q&A System SHALL block the link and display an error
3. THE Q&A System SHALL whitelist only http and https URL schemes
4. WHEN a user flags a question or answer, THE Q&A System SHALL add it to the admin moderation queue
5. THE Q&A System SHALL sanitize all user-generated content before rendering

### Requirement 11: Book Details Enhancement

**User Story:** As a user, I want to view multiple images with proper accessibility, so that I can see detailed product photos

#### Acceptance Criteria

1. WHEN a book details page loads, THE Catalog System SHALL display all available images with lazy loading
2. THE Catalog System SHALL include alt text for each image containing the book title and author
3. THE Catalog System SHALL specify explicit width and height attributes for all images
4. WHEN images are outside the viewport, THE Catalog System SHALL defer loading until the user scrolls
5. THE Catalog System SHALL display a related books section based on genre or author
