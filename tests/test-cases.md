This document outlines key functional and non-functional test cases.

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
Screenshot/GIF paths:<img width="1913" height="866" alt="search" src="https://github.com/user-attachments/assets/8c883f8c-3aa2-4012-93d2-9fb85a306aef" />


ID:TC-002

## Tittle:Redirect from root to catalog

## Pre-conditions:
App running at /; user role irrelevant
Steps:

i.Navigate to /

## Expected Result: User is redirected to /catalog

## Post-conditions: URL changes to /catalog

## Evidence:
Screenshot of /catalog page: ![Uploading catalog.png…]()




## ID: TC-003

## Title: Add book to cart from catalog

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






