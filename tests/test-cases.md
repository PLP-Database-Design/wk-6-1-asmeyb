# ✅ Test Cases – Book Store App QA Project  
**Team:** `PLP Testers`  
**Last updated:** – `2025-11-11`

---

### TC-001 – Search by Partial Title (Case-Insensitive)
**Pre-conditions:**  
Catalog contains a book titled “The Great Gatsby”.

**Steps:**  
1. Navigate to `/catalog`.  
2. Enter query with mixed case and extra spaces: `"  the Great gatsby "`.  
3. Press Enter or click Search icon.

**Expected Result:**  
Catalog displays only the matching book; no error toast.

**Post-conditions:**  
Search input retains the trimmed query.

**Evidence:**  
![search](https://github.com/user-attachments/assets/8c883f8c-3aa2-4012-93d2-9fb85a306aef)

---

### TC-002 – Redirect from Root to Catalog
**Pre-conditions:**  
App running at `http://localhost:3000/`.

**Steps:**  
1. Open browser and navigate to `/`.

**Expected Result:**  
URL changes to `/catalog` without full page reload.

**Post-conditions:**  
Catalog page renders.

**Evidence:**  
![catalog](https://github.com/user-attachments/assets/af85a029-1bbd-4ee5-ba56-4fc931a285a4)

---

### TC-003 – Add Book to Cart from Catalog
**Pre-conditions:**  
Catalog loaded; at least one book visible.

**Steps:**  
1. Click “Buy Now” on any book.

**Expected Result:**  
Cart badge increments by 1; book appears in cart.

**Post-conditions:**  
`app.cart` key in localStorage updated.

**Evidence:**  
Screenshot of badge + localStorage :<img width="1903" height="927" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/011b793c-509d-4eb8-a48b-8816ff372d83" />


---

### TC-004 – Update Quantity in Cart
**Pre-conditions:**  
Cart contains ≥1 book.

**Steps:**  
1. Go to `/cart`.  
2. Click “+” to increment quantity.

**Expected Result:**  
Subtotal recalculates correctly (rounded to 2 decimals).

**Post-conditions:**  
`app.cart` updated.

**Evidence:**  
Screenshot of updated subtotal: <img width="1899" height="901" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/0fc3690f-6508-4efa-aa31-567db4e1f7e2" />



---

### TC-005 – Remove Book from Cart
**Pre-conditions:**  
Cart contains ≥1 book.

**Steps:**  
1. Click “Remove” button on a line item.

**Expected Result:**  
Item disappears; subtotal updates; if last item, cart shows empty state.

**Post-conditions:**  
`app.cart` updated.

**Evidence:**  
Screenshot of empty-cart state.:<img width="1920" height="1080" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/e6f2402a-3955-4a97-aeb2-792a5e64571a" />



## ID: TC-006
## Title: Navigate to checkout wizard
**pre-condititions**:
Cart contains books
## Steps:

i.Go to catalog
ii.select by any book
iii.click checkout
**Expected Result**: 
Checkout wizard loads with cart summary
**Post-conditions**: 
checkout details 
**Evidence**: 
Screenshot of checkout :<img width="1887" height="939" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/4fbf76ce-867e-4fcb-a88f-6b4d46cca52c" />


## ID: TC-007
## Title: Mock payment via Paystack test card
**Pre-conditions**: 
Checkout page loaded with items; test mode active
 **Steps**:

i.Enter Paystack test card number 4084084084084081

ii.Enter CVV, expiry, and PIN

iii.Submit payment

**Expected Result**:
Payment success flow triggered

**Post-conditions**: 
app.orders updated in localStorage

**Evidence**: 
Screenshot of payment success confirmation

## ID: TC-008
## Title: Access admin page as admin

**Pre-conditions**: 
localStorage.setItem('app.user', JSON.stringify({ role: 'admin' }))

**Steps**:

Navigate to /admin
**Expected Result**: 
Admin page content displayed

**Post-conditions**:
None

**Evidence**: 
Screenshot of admin console

## ID: TC-009
## Title: Cart persistence after reload

**Pre-conditions**: 
Cart contains books
## Steps:

i.Reload /cart page
**Expected Result**:
Items remain in cart after reload
**Post-conditions**: 
app.cart persisted in localStorage
 **Evidence**: 
Screenshot of cart after reload:<img width="1904" height="882" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/0b3db5dc-a2c3-4756-9b3e-90fa88c54fa4" />


## ID: TC-010
## Title: Checkout without items in cart
**Pre-conditions**: 
Cart is empty
**Steps**:

i.Navigate to /checkout
**Expected Result**: 
Warning/error message displayed; your cart is empty

**Post-conditions**:
None

**Evidence**:
Screenshot of warning message:<img width="1904" height="882" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/168a2e28-3a6a-4c07-934d-3ebfeeb615ab" />


## ID: TC-011
## Title: Currency displayed matches Paystack util
**Pre-conditions**: 
Checkout with currency set (e.g., NGN)

**Steps**:

i.View total in cart or checkout page

## Expected Result: 
Displayed currency matches Paystack currency setting

**Post-conditions**: 
None

**Evidence**:
Screenshot of currency display


##  A. Manual Test Scripts

| **TC ID** | **Title**                                  | **Pre-conditions**                               | **Test Steps**                                                                       | **Expected Result**                                                  | **Post-conditions**                |
| --------- | ------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------- | ---------------------------------- |
| TC-001    | Search by Partial Title (Case-Insensitive) | Catalog contains “The Great Gatsby”              | 1. Navigate to `/catalog` <br> 2. Enter `"  the Great gatsby "` <br> 3. Click Search | Only *The Great Gatsby* displayed; no errors; trimmed query retained | None                               |
| TC-002    | Redirect from Root to Catalog              | App running on `localhost:3000`                  | 1. Navigate to `/`                                                                   | Redirects to `/catalog` without full reload                          | Catalog page loaded                |
| TC-003    | Add Book to Cart                           | Catalog loaded with books                        | 1. Click “Buy Now”                                                                   | Cart badge increments; book appears in cart                          | `app.cart` in localStorage updated |
| TC-004    | Update Quantity in Cart                    | Cart has ≥1 book                                 | 1. Go to `/cart` <br> 2. Click “+”                                                   | Subtotal recalculates correctly (2 decimals)                         | localStorage updated               |
| TC-005    | Remove Book from Cart                      | Cart has ≥1 book                                 | 1. Click “Remove”                                                                    | Item disappears; subtotal updates; empty state if last item          | localStorage updated               |
| TC-006    | Navigate to Checkout Wizard                | Cart contains books                              | 1. Go to `/catalog` <br> 2. Click “Buy Now” <br> 3. Click “Checkout”                 | Checkout wizard loads with cart summary                              | Checkout details visible           |
| TC-007    | Mock Payment via Paystack Test Card        | Checkout page open, test mode active             | 1. Enter card `4084084084084081` <br> 2. Enter CVV, expiry, PIN <br> 3. Submit       | Payment success flow triggered                                       | `app.orders` updated               |
| TC-008    | Access Admin Page as Admin                 | `app.user` = `{ role: 'admin' }` in localStorage | 1. Navigate to `/admin`                                                              | Admin console displays                                               | None                               |
| TC-009    | Cart Persistence After Reload              | Cart has books                                   | 1. Reload `/cart`                                                                    | Items persist after reload                                           | localStorage persists              |
| TC-010    | Checkout Without Items in Cart             | Cart empty                                       | 1. Navigate to `/checkout`                                                           | Warning message: “Your cart is empty.”                               | None                               |
| TC-011    | Currency Display Matches Paystack Util     | Currency = NGN                                   | 1. View total in cart or checkout                                                    | Currency symbol/format matches Paystack                              | None                               |

---

## 🤖 B. Automated Test Scripts (Cypress)

```javascript
describe('📚 Book Store App – PLP Testers Suite', () => {

  beforeEach(() => {
    cy.viewport(1280, 720);
  });

  it('TC-001: Search by Partial Title (Case-Insensitive)', () => {
    cy.visit('/catalog');
    cy.get('input[placeholder="Search"]').type('  the Great gatsby ');
    cy.get('button[data-testid="search"]').click();
    cy.contains('The Great Gatsby').should('be.visible');
    cy.get('input[placeholder="Search"]').should('have.value', 'the Great gatsby');
  });

  it('TC-002: Redirect from Root to Catalog', () => {
    cy.visit('/');
    cy.url().should('include', '/catalog');
    cy.contains('Catalog').should('exist');
  });

  it('TC-003: Add Book to Cart', () => {
    cy.visit('/catalog');
    cy.get('button').contains('Buy Now').first().click();
    cy.get('[data-testid="cart-badge"]').should('contain', '1');
    cy.window().then(win => {
      const cart = JSON.parse(win.localStorage.getItem('app.cart'));
      expect(cart).to.have.length(1);
    });
  });

  it('TC-004: Update Quantity in Cart', () => {
    cy.visit('/cart');
    cy.get('[data-testid="qty-plus"]').first().click();
    cy.get('[data-testid="subtotal"]').invoke('text').then(text => {
      const subtotal = parseFloat(text.replace(/[^\d.]/g, ''));
      expect(subtotal).to.be.greaterThan(0);
    });
  });

  it('TC-005: Remove Book from Cart', () => {
    cy.visit('/cart');
    cy.get('button').contains('Remove').first().click();
    cy.get('[data-testid="cart-empty"]').should('be.visible');
  });

  it('TC-006: Navigate to Checkout Wizard', () => {
    cy.visit('/catalog');
    cy.get('button').contains('Buy Now').first().click();
    cy.get('button').contains('Checkout').click();
    cy.url().should('include', '/checkout');
    cy.contains('Order Summary').should('exist');
  });

  it('TC-007: Mock Payment via Paystack Test Card', () => {
    cy.visit('/checkout');
    cy.get('input[name="cardNumber"]').type('4084084084084081');
    cy.get('input[name="expiry"]').type('12/30');
    cy.get('input[name="cvv"]').type('123');
    cy.get('button').contains('Pay').click();
    cy.contains('Payment Successful').should('exist');
    cy.window().then(win => {
      const orders = JSON.parse(win.localStorage.getItem('app.orders'));
      expect(orders).to.have.length.greaterThan(0);
    });
  });

  it('TC-008: Access Admin Page as Admin', () => {
    cy.window().then(win => {
      win.localStorage.setItem('app.user', JSON.stringify({ role: 'admin' }));
    });
    cy.visit('/admin');
    cy.contains('Admin Dashboard').should('be.visible');
  });

  it('TC-009: Cart Persistence After Reload', () => {
    cy.visit('/cart');
    cy.reload();
    cy.get('[data-testid="cart-item"]').should('exist');
  });

  it('TC-010: Checkout Without Items in Cart', () => {
    cy.window().then(win => {
      win.localStorage.setItem('app.cart', JSON.stringify([]));
    });
    cy.visit('/checkout');
    cy.contains('Your cart is empty').should('be.visible');
  });

  it('TC-011: Currency Display Matches Paystack Util', () => {
    cy.visit('/checkout');
    cy.contains('NGN').should('exist'); // or check currency symbol ₦
  });

});
```

---















