&lt;!-- tests/test-cases.md --&gt;
# ✅ Test Cases – Book Store App QA Project  
**Team:** `&lt;PLP Testers&gt;`  
**Last updated:– 2025-11-11

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
Screenshot of badge + localStorage (to be attached during execution).

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
Screenshot of updated subtotal.

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
Screenshot of empty-cart state.