# Design Document

## Overview

This design addresses the 26 failed test cases identified in QA testing by implementing missing features across catalog management, cart validation, coupon system, order management, admin functionality, and user-generated content. The design maintains the existing React 18 + localStorage architecture while adding new data models, services, and UI components.

The implementation follows the existing patterns:
- Global state management via StoreContext
- localStorage persistence with safe helpers
- React Router 6 for navigation
- Tailwind CSS for styling
- Functional components with hooks

## Architecture

### High-Level Component Structure

```
┌─────────────────────────────────────────────────────────────┐
│                      StoreProvider                          │
│  (Global State: cart, orders, coupons, reviews, inventory)  │
└─────────────────────────────────────────────────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
┌───────▼────────┐  ┌──────▼──────┐  ┌────────▼────────┐
│  CatalogPage   │  │  CartPage   │  │  CheckoutPage   │
│  + Filters     │  │  + Stock    │  │  + Coupons      │
│  + Sorting     │  │  Validation │  │                 │
└────────────────┘  └─────────────┘  └─────────────────┘
        │
┌───────▼────────┐  ┌──────────────┐  ┌────────────────┐
│ BookDetailPage │  │ OrdersPage   │  │  AdminConsole  │
│ + Reviews      │  │ + CSV Export │  │  + CRUD        │
│ + Q&A          │  │ + Returns    │  │  + Inventory   │
│ + Multi-images │  │              │  │  + Moderation  │
└────────────────┘  └──────────────┘  └────────────────┘
```

### Service Layer

```
Services/
├── FilterService.js      - Catalog filtering and sorting logic
├── CouponService.js      - Coupon validation and application
├── OrderService.js       - Order lifecycle and CSV export
├── ReviewService.js      - Review CRUD and sanitization
├── InventoryService.js   - Stock management and validation
└── AuditService.js       - Audit trail logging
```

## Components and Interfaces

### 1. Enhanced Book Data Model

```javascript
{
  id: number,
  title: string,
  author: string,
  price: number,
  image: string,
  description: string,
  // NEW FIELDS
  genre: string,              // "Fiction", "Non-Fiction", "Mystery", etc.
  rating: number,             // 0-5 stars
  popularity: number,         // View/purchase count
  stock: number,              // Available quantity
  images: string[],           // Multiple product images
  isbn: string,
  dimensions: string,
  tags: string[],
  featured: boolean
}
```

### 2. Coupon Data Model

```javascript
{
  code: string,               // "SAVE20"
  type: 'percent' | 'fixed', // Discount type
  amount: number,             // 20 or 5.00
  minBasket: number,          // Minimum order subtotal
  combinable: boolean,        // Can combine with other coupons
  validFrom: string,          // ISO8601 date
  validTo: string,            // ISO8601 date
  active: boolean
}
```

### 3. Review Data Model

```javascript
{
  id: string,
  bookId: number,
  userId: string,
  userName: string,
  rating: number,             // 1-5 stars
  title: string,
  content: string,            // Sanitized HTML
  purchaseVerified: boolean,
  helpful: number,            // Helpful votes
  flagged: boolean,
  flagReason: string,
  createdAt: string,          // ISO8601
  updatedAt: string
}
```

### 4. Q&A Data Model

```javascript
{
  id: string,
  bookId: number,
  type: 'question' | 'answer',
  parentId: string,           // For answers
  userId: string,
  userName: string,
  content: string,            // Sanitized markdown
  flagged: boolean,
  createdAt: string
}
```

### 5. Audit Entry Data Model

```javascript
{
  id: string,
  entityType: string,         // "order", "inventory", "review"
  entityId: string,
  action: string,             // "status_change", "refund", "stock_adjustment"
  by: string,                 // User ID or "system"
  note: string,
  metadata: object,           // Additional context
  at: string                  // ISO8601 timestamp
}
```

### 6. Order Enhancement

```javascript
{
  // ... existing fields
  status: 'Pending' | 'Paid' | 'Fulfilled' | 'Delivered' | 'Cancelled' | 'Refunded',
  appliedCoupons: Coupon[],
  returnRequest: {
    requestedAt: string,
    reason: string,
    status: 'pending' | 'approved' | 'rejected'
  },
  refund: {
    amount: number,
    processedAt: string,
    processedBy: string,
    reason: string
  },
  audit: AuditEntry[]
}
```

## Data Models

### FilterState

```javascript
{
  search: string,
  genres: string[],           // Selected genres
  priceRange: {
    min: number,
    max: number
  },
  minRating: number,          // 0-5
  sortBy: 'price' | 'rating' | 'popularity',
  sortOrder: 'asc' | 'desc'
}
```

### InventoryItem

```javascript
{
  bookId: number,
  stock: number,
  lowStockThreshold: number,  // Default: 5
  lastUpdated: string,
  updatedBy: string
}
```

## Error Handling

### Validation Errors

All validation errors follow a consistent structure:

```javascript
{
  field: string,              // Field name
  message: string,            // User-friendly error
  code: string                // Error code for i18n
}
```

### Error Scenarios

1. **Stock Validation**
   - Quantity exceeds stock → Display: "Only X items available"
   - Out of stock → Disable "Buy Now" button

2. **Coupon Validation**
   - Expired → "This coupon expired on [date]"
   - Below minimum → "Minimum order of [amount] required"
   - Not combinable → "This coupon cannot be combined with other discounts"

3. **Review Validation**
   - Not a purchaser → "Only verified purchasers can review this book"
   - Duplicate review → "You've already reviewed this book"
   - XSS detected → "Invalid content detected. Please remove scripts or unsafe links"

4. **Return Validation**
   - Outside window → "Returns are only accepted within 7 days of delivery"
   - Invalid status → "This order cannot be returned"

### Error Display Strategy

- Inline errors: Form validation, cart operations
- Toast notifications: Success/failure of async operations
- Modal dialogs: Critical errors requiring acknowledgment
- aria-live regions: Screen reader announcements

## Testing Strategy

### Unit Tests

1. **FilterService**
   - Genre filtering with multiple selections
   - Price range boundary conditions
   - Rating threshold filtering
   - Sort stability and tie-breakers
   - Combined filter logic (AND semantics)

2. **CouponService**
   - Date validation (expired, not yet valid)
   - Minimum basket enforcement
   - Combinability rules
   - Discount calculation (percent vs fixed)

3. **ReviewService**
   - Purchase verification
   - Duplicate detection
   - XSS sanitization
   - URL scheme validation

4. **InventoryService**
   - Stock validation
   - Low-stock threshold detection
   - Concurrent update handling

### Integration Tests

1. **Catalog Flow**
   - Apply filters → verify results
   - Change sort → verify order
   - Clear filters → restore full list

2. **Cart Flow**
   - Add item → validate stock
   - Increase quantity → enforce limit
   - Stock changes → revalidate cart

3. **Checkout Flow**
   - Apply coupon → verify discount
   - Remove coupon → restore total
   - Multiple coupons → enforce rules

4. **Order Flow**
   - Status transitions → audit trail
   - Request return → validate window
   - Process refund → update status

### E2E Tests (Cypress)

1. Complete purchase with coupon
2. Admin updates order status
3. User submits and edits review
4. Admin processes return/refund
5. CSV export and validation

## Implementation Details

### 1. Catalog Filtering and Sorting

**Component: FilterPanel.js**

```javascript
// Filter UI with checkboxes for genres, price slider, rating selector
// Emits filter changes to parent CatalogPage
```

**Service: FilterService.js**

```javascript
export const applyFilters = (books, filterState) => {
  let filtered = [...books];
  
  // Search
  if (filterState.search) {
    const query = filterState.search.toLowerCase().trim();
    filtered = filtered.filter(book => 
      book.title.toLowerCase().includes(query) ||
      book.author.toLowerCase().includes(query) ||
      book.description.toLowerCase().includes(query)
    );
  }
  
  // Genre filter (OR within genres)
  if (filterState.genres.length > 0) {
    filtered = filtered.filter(book => 
      filterState.genres.includes(book.genre)
    );
  }
  
  // Price range
  if (filterState.priceRange) {
    filtered = filtered.filter(book =>
      book.price >= filterState.priceRange.min &&
      book.price <= filterState.priceRange.max
    );
  }
  
  // Rating threshold
  if (filterState.minRating > 0) {
    filtered = filtered.filter(book => 
      book.rating >= filterState.minRating
    );
  }
  
  return filtered;
};

export const applySorting = (books, sortBy, sortOrder) => {
  const sorted = [...books];
  
  sorted.sort((a, b) => {
    let comparison = 0;
    
    switch (sortBy) {
      case 'price':
        comparison = a.price - b.price;
        break;
      case 'rating':
        comparison = b.rating - a.rating; // Higher rating first
        break;
      case 'popularity':
        comparison = b.popularity - a.popularity;
        break;
      default:
        comparison = 0;
    }
    
    return sortOrder === 'desc' ? -comparison : comparison;
  });
  
  return sorted;
};
```

### 2. Stock Validation

**Service: InventoryService.js**

```javascript
export const validateCartQuantity = (bookId, requestedQty, inventory) => {
  const item = inventory.find(i => i.bookId === bookId);
  
  if (!item) {
    return { valid: false, error: 'Book not found in inventory' };
  }
  
  if (item.stock === 0) {
    return { valid: false, error: 'Out of stock' };
  }
  
  if (requestedQty > item.stock) {
    return { 
      valid: false, 
      error: `Only ${item.stock} items available`,
      maxQuantity: item.stock
    };
  }
  
  return { valid: true };
};

export const isLowStock = (bookId, inventory) => {
  const item = inventory.find(i => i.bookId === bookId);
  return item && item.stock <= item.lowStockThreshold;
};
```

**Enhanced addToCart in StoreProvider**

```javascript
const addToCart = useCallback((book, quantity = 1) => {
  // Validate stock
  const validation = validateCartQuantity(book.id, quantity, inventory);
  
  if (!validation.valid) {
    // Show error toast
    addNotification({
      type: 'error',
      message: validation.error
    });
    return false;
  }
  
  setCart((prev) => {
    const existing = prev.find((i) => i.id === book.id);
    if (existing) {
      const newQty = existing.quantity + quantity;
      const revalidation = validateCartQuantity(book.id, newQty, inventory);
      
      if (!revalidation.valid) {
        addNotification({
          type: 'error',
          message: revalidation.error
        });
        return prev; // Don't update
      }
      
      return prev.map((i) => 
        i.id === book.id ? { ...i, quantity: newQty } : i
      );
    }
    return [...prev, { id: book.id, book, quantity }];
  });
  
  return true;
}, [inventory]);
```

### 3. Coupon System

**Service: CouponService.js**

```javascript
export const validateCoupon = (coupon, subtotal, appliedCoupons) => {
  // Check if active
  if (!coupon.active) {
    return { valid: false, error: 'This coupon is not active' };
  }
  
  // Check dates
  const now = new Date();
  const validFrom = new Date(coupon.validFrom);
  const validTo = new Date(coupon.validTo);
  
  if (now < validFrom) {
    return { valid: false, error: 'This coupon is not yet valid' };
  }
  
  if (now > validTo) {
    return { 
      valid: false, 
      error: `This coupon expired on ${validTo.toLocaleDateString()}` 
    };
  }
  
  // Check minimum basket
  if (coupon.minBasket && subtotal < coupon.minBasket) {
    return { 
      valid: false, 
      error: `Minimum order of ${formatCurrency(coupon.minBasket)} required` 
    };
  }
  
  // Check combinability
  if (!coupon.combinable && appliedCoupons.length > 0) {
    return { 
      valid: false, 
      error: 'This coupon cannot be combined with other discounts' 
    };
  }
  
  if (appliedCoupons.some(c => !c.combinable)) {
    return { 
      valid: false, 
      error: 'Cannot combine with existing non-combinable coupon' 
    };
  }
  
  // Check duplicate
  if (appliedCoupons.some(c => c.code === coupon.code)) {
    return { valid: false, error: 'Coupon already applied' };
  }
  
  return { valid: true };
};

export const calculateDiscount = (coupon, subtotal) => {
  if (coupon.type === 'percent') {
    return (subtotal * coupon.amount) / 100;
  }
  return coupon.amount;
};

export const applyAllCoupons = (coupons, subtotal) => {
  return coupons.reduce((total, coupon) => {
    return total - calculateDiscount(coupon, subtotal);
  }, subtotal);
};
```

### 4. Order Management and CSV Export

**Service: OrderService.js**

```javascript
export const updateOrderStatus = (order, newStatus, userId, note = '') => {
  const validTransitions = {
    'Pending': ['Paid', 'Cancelled'],
    'Paid': ['Fulfilled', 'Cancelled', 'Refunded'],
    'Fulfilled': ['Delivered', 'Cancelled'],
    'Delivered': ['Refunded'],
    'Cancelled': [],
    'Refunded': []
  };
  
  if (!validTransitions[order.status].includes(newStatus)) {
    return { 
      success: false, 
      error: `Cannot transition from ${order.status} to ${newStatus}` 
    };
  }
  
  const auditEntry = {
    id: generateId(),
    entityType: 'order',
    entityId: order.id,
    action: 'status_change',
    by: userId,
    note,
    metadata: { from: order.status, to: newStatus },
    at: new Date().toISOString()
  };
  
  return {
    success: true,
    updatedOrder: {
      ...order,
      status: newStatus,
      audit: [...(order.audit || []), auditEntry]
    }
  };
};

export const exportOrdersToCSV = (orders) => {
  const headers = [
    'Order ID',
    'Date',
    'Status',
    'Customer Email',
    'Items',
    'Subtotal',
    'Shipping',
    'Tax',
    'Total',
    'Gateway Reference'
  ];
  
  const rows = orders.map(order => [
    order.id,
    order.createdAt,
    order.status,
    order.shipping.email,
    order.items.length,
    order.totals.subtotal.toFixed(2),
    order.totals.shippingFee.toFixed(2),
    order.totals.tax.toFixed(2),
    order.totals.total.toFixed(2),
    order.gatewayRef || ''
  ]);
  
  const csvContent = [
    headers.join(','),
    ...rows.map(row => row.map(cell => `"${cell}"`).join(','))
  ].join('\n');
  
  return new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
};
```

### 5. Review System with Sanitization

**Service: ReviewService.js**

```javascript
import DOMPurify from 'dompurify';

export const canUserReview = (userId, bookId, orders) => {
  return orders.some(order => 
    order.status === 'Delivered' &&
    order.items.some(item => item.book.id === bookId)
  );
};

export const hasUserReviewed = (userId, bookId, reviews) => {
  return reviews.some(review => 
    review.userId === userId && review.bookId === bookId
  );
};

export const sanitizeReviewContent = (content) => {
  // Configure DOMPurify
  const config = {
    ALLOWED_TAGS: ['b', 'i', 'em', 'strong', 'p', 'br'],
    ALLOWED_ATTR: [],
    KEEP_CONTENT: true
  };
  
  return DOMPurify.sanitize(content, config);
};

export const validateReview = (review, userId, bookId, orders, reviews) => {
  // Check purchase
  if (!canUserReview(userId, bookId, orders)) {
    return { 
      valid: false, 
      error: 'Only verified purchasers can review this book' 
    };
  }
  
  // Check duplicate
  if (hasUserReviewed(userId, bookId, reviews)) {
    return { 
      valid: false, 
      error: "You've already reviewed this book" 
    };
  }
  
  // Validate rating
  if (review.rating < 1 || review.rating > 5) {
    return { valid: false, error: 'Rating must be between 1 and 5' };
  }
  
  // Sanitize content
  const sanitized = sanitizeReviewContent(review.content);
  
  return { 
    valid: true, 
    sanitizedContent: sanitized 
  };
};
```

### 6. Q&A with Safe Markdown

**Service: QAService.js**

```javascript
import { marked } from 'marked';
import DOMPurify from 'dompurify';

export const sanitizeMarkdown = (markdown) => {
  // Configure marked
  marked.setOptions({
    breaks: true,
    gfm: true
  });
  
  // Convert markdown to HTML
  const html = marked.parse(markdown);
  
  // Sanitize with strict rules
  const config = {
    ALLOWED_TAGS: ['p', 'br', 'strong', 'em', 'ul', 'ol', 'li', 'a', 'code', 'pre'],
    ALLOWED_ATTR: ['href'],
    ALLOWED_URI_REGEXP: /^https?:\/\//,
    KEEP_CONTENT: true
  };
  
  return DOMPurify.sanitize(html, config);
};

export const validateURL = (url) => {
  try {
    const parsed = new URL(url);
    return ['http:', 'https:'].includes(parsed.protocol);
  } catch {
    return false;
  }
};
```

### 7. Return and Refund Processing

**Service: ReturnService.js**

```javascript
export const canRequestReturn = (order) => {
  if (order.status !== 'Delivered') {
    return { allowed: false, reason: 'Order must be delivered to request return' };
  }
  
  // Calculate days since delivery
  const deliveredDate = order.audit
    .filter(a => a.action === 'status_change' && a.metadata.to === 'Delivered')
    .sort((a, b) => new Date(b.at) - new Date(a.at))[0];
  
  if (!deliveredDate) {
    return { allowed: false, reason: 'Delivery date not found' };
  }
  
  const daysSince = Math.floor(
    (new Date() - new Date(deliveredDate.at)) / (1000 * 60 * 60 * 24)
  );
  
  if (daysSince > 7) {
    return { 
      allowed: false, 
      reason: 'Returns are only accepted within 7 days of delivery' 
    };
  }
  
  return { allowed: true, daysRemaining: 7 - daysSince };
};

export const processRefund = (order, amount, userId, reason) => {
  const auditEntry = {
    id: generateId(),
    entityType: 'order',
    entityId: order.id,
    action: 'refund',
    by: userId,
    note: reason,
    metadata: { amount, type: amount === order.totals.total ? 'full' : 'partial' },
    at: new Date().toISOString()
  };
  
  return {
    ...order,
    status: 'Refunded',
    refund: {
      amount,
      processedAt: new Date().toISOString(),
      processedBy: userId,
      reason
    },
    audit: [...(order.audit || []), auditEntry]
  };
};
```

## UI Component Structure

### New Components

1. **FilterPanel.js** - Sidebar with genre, price, rating filters
2. **SortControls.js** - Dropdown for sort options
3. **CouponInput.js** - Coupon code input with validation feedback
4. **ReviewForm.js** - Star rating + text input with sanitization
5. **ReviewList.js** - Display reviews with flag/helpful buttons
6. **QASection.js** - Questions and answers with markdown support
7. **OrderStatusTimeline.js** - Visual status progression
8. **ReturnRequestForm.js** - Return reason and validation
9. **AdminInventoryPanel.js** - Stock adjustment interface
10. **AdminModerationQueue.js** - Flagged content review
11. **BookImageGallery.js** - Multiple images with lazy loading
12. **LowStockBadge.js** - Warning indicator for low inventory

### Enhanced Components

1. **CatalogPage.js** - Add FilterPanel and SortControls
2. **CartPage.js** - Add stock validation feedback
3. **CheckoutPage.js** - Add CouponInput component
4. **BookDetailPage.js** - Add ReviewList, QASection, ImageGallery
5. **OrderDetailPage.js** - Add StatusTimeline, ReturnRequestForm
6. **AdminPage.js** - Add tabs for Inventory, Orders, Moderation

## Security Considerations

### XSS Prevention

1. **Review Content**: Use DOMPurify with strict whitelist
2. **Q&A Markdown**: Validate URL schemes, strip javascript:
3. **User Input**: Sanitize all UGC before storage and display

### URL Validation

```javascript
const SAFE_PROTOCOLS = ['http:', 'https:'];

export const isSafeURL = (url) => {
  try {
    const parsed = new URL(url);
    return SAFE_PROTOCOLS.includes(parsed.protocol);
  } catch {
    return false;
  }
};
```

### Storage Security

- No PII beyond test emails
- Audit trails are append-only
- Admin actions require role verification

## Performance Optimizations

1. **Lazy Loading**: Images load only when in viewport
2. **Memoization**: Filter/sort results cached with useMemo
3. **Debouncing**: Search input debounced 300ms
4. **Virtual Scrolling**: For large review lists (future)
5. **Code Splitting**: Admin components loaded on-demand

## Accessibility

1. **ARIA Labels**: All interactive elements labeled
2. **Focus Management**: Modal traps focus, returns on close
3. **Keyboard Navigation**: Tab order logical, ESC closes modals
4. **Screen Reader**: aria-live for dynamic updates
5. **Color Contrast**: WCAG 2.1 AA compliant
6. **Reduce Motion**: Respect prefers-reduced-motion

## Migration Strategy

### Phase 1: Data Model Updates
- Extend books.js with new fields
- Add seed data for genres, ratings, stock
- Initialize inventory in StoreProvider

### Phase 2: Core Services
- Implement FilterService, CouponService, InventoryService
- Add validation to cart operations
- Update CheckoutService for coupons

### Phase 3: UI Components
- Build FilterPanel, CouponInput
- Enhance CatalogPage, CartPage, CheckoutPage
- Add stock validation feedback

### Phase 4: Order Management
- Implement OrderService with status transitions
- Add CSV export functionality
- Build admin order dashboard

### Phase 5: UGC Features
- Implement ReviewService, QAService
- Build review and Q&A components
- Add moderation queue

### Phase 6: Admin Features
- Build inventory management UI
- Add catalog CRUD operations
- Implement return/refund processing

## Testing Checkpoints

After each phase:
1. Run affected test cases from test-cases.md
2. Verify no regressions in existing features
3. Update traceability matrix
4. Document any deviations or issues
