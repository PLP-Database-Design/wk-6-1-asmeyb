<img width="1896" height="967" alt="catalog" src="https://github.com/user-attachments/assets/af85a029-1bbd-4ee5-ba56-4fc931a285a4" />This document outlines key functional and non-functional test cases.

ID: TC-001

## Title: Search by Partial Title (Case-Insensitive)

Pre-conditions: Catalog contains a book titled “The Great Gatsby.”

## Steps:

i.Navigate to the Catalog page (/catalog).

ii.Enter a partial mixed-case query: "  the Great gatsby ".

iii.Press Enter or click Search.

## Expected Result:
The catalog view updates to show only the matching book (“The Great Adventure of QA”). No error message displayed.

## Post-conditions:
Search query remains visible in the search bar.

## Evidence:
<<<<<<< HEAD
Screenshot/GIF paths:
<img width="1913" height="866" alt="search" src="https://github.com/user-attachments/assets/8c883f8c-3aa2-4012-93d2-9fb85a306aef" />

=======
Screenshot/GIF paths:<img width="1913" height="866" alt="search" src="https://github.com/user-attachments/assets/8c883f8c-3aa2-4012-93d2-9fb85a306aef" />
>>>>>>> bfb73f85c2a8fc2265f56293a686ff37d2bb9390


ID:TC-002

## Tittle:Redirect from root to catalog

<<<<<<< HEAD
## Pre-conditions: App running at /; user role irrelevant
=======
## Pre-conditions:
App running at /; user role irrelevant
>>>>>>> bfb73f85c2a8fc2265f56293a686ff37d2bb9390
Steps:

i.Navigate to /

## Expected Result: User is redirected to /catalog

## Post-conditions: URL changes to /catalog

<<<<<<< HEAD
## Evidence: Screenshot of /catalog page:![Uploading catalog.png…]()
=======
## Evidence:
Screenshot of /catalog page:<img width="1896" height="967" alt="catalog" src="https://github.com/user-attachments/assets/b0a34cf2-35ff-48a3-970c-cc271185624c" />


>>>>>>> bfb73f85c2a8fc2265f56293a686ff37d2bb9390



## ID: TC-003

## Title: Add book to cart from catalog

<<<<<<< HEAD
## Pre-conditions: Catalog page loaded, all book visible

## Steps:
i.Open the bookstore catalog
ii.Click “Buy Now” on a book

## Expected Result: Book is added to cart; cart badge increments

## Post-conditions: app.cart in localStorage updated

## Evidence: Screenshot of cart badge and localStorage
=======
## Pre-conditions: 
Catalog is loaded ,all books visible

## Steps:
i.Open the bookstore catalog
ii.Click “Buy Now” on a book.

## Expected Result: 
Book is added to cart; cart badge increments

## Post-conditions: 
app.cart in localStorage updated

## Evidence:
Screenshot of cart badge and localStorage:

ID: TC-004
## Title: Update quantity in cart
## Pre-conditions:
Cart contains at least one book
## Steps:

i.Go to /cart
ii.Increment quantity of a book
## Expected Result:
Subtotal updates correctly
## Post-conditions: 
app.cart  updated
## Evidence: 
Screenshot of updated subtotal

ID: TC-005
## Title: Remove book from cart
## Pre-conditions:
Cart contains at least one book
## Steps:
i.Open the cart
ii.Click “Remove” on a book
## Expected Result: 
Book disappears from cart; subtotal updates
## Post-conditions: 
app.cart  updated
## Evidence: 
Screenshot showing updated or empty cart








>>>>>>> bfb73f85c2a8fc2265f56293a686ff37d2bb9390

