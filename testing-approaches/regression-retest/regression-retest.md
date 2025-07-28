# Regression testing - Shopping Cart

##  Table of contents

1. [Introduction](#1-introduction)
2. [Re-test test cases](#2-re-test-test-cases)
3. [Regression test cases](#3-regression-test-cases)
4. [Bug reports](#4-bug-reports)
    1. [MSB-001 - Cannot modify product quantity from cart](#msb-001---cannot-modify-product-quantity-from-cart)
    2. [MSB-002 - Quantity input accepts negative or zero values and allows checkout with invalid total](#msb-002---quantity-input-accepts-negative-or-zero-values-and-allows-checkout-with-invalid-total)
    3. [MSB-003 - Footer copyright year outdated](#msb-003---footer-copyright-year-outdated)
    4. [MSB-004 - Inconsistent product card sizes affect page layout](#msb-004---inconsistent-product-card-sizes-affect-page-layout)

## 1. Introduction
- **Website:** [https://automationexercise.com/](https://automationexercise.com/)
- **Bug:** When users added two units of the same product, the cart displayed only the price of one.
- **Fix Applied:** Code was updated to multiply the product price by quantity.
- **Objective:**
    - Verify that the original bug is fixed by performing re-tests
    - Run regression tests to ensure other functionalities related to the cart were not broken.

## 2. Re-test test cases

| Test Case Title | Test Steps | Test Data | Expected Result | Why Included (Scope/Reasoning) |
|------------------|------------|-----------|------------------|-------------------------------|
| Verify that adding 2 items of the same product from the product list updates the cart total correctly | 1. Go to homepage  <br> 2. Find any product <br> 3. Click “Add to cart” <br> 4. Click on “Continue shopping” button <br> 5. Click on “Add to cart” for the same product <br> 6. Click on “View Cart” button <br> 7. Check product price and the order Total | Any product from the product list | The cart should show 2 units of the selected product, and the total price should be the unit price times 2 | Verifies that the original bug related to quantity calculation when adding the same item twice has been fixed correctly |
| Verify that adding two units from the product detail page updates the cart total correctly | 1. Go to homepage <br> 2. Find any product <br> 3. Click on “View product” button on the product card <br> 4. Enter “2” on “Quantity” <br> 5. Click on “Add to cart” button <br> 6. Click on “View Cart” button <br> 7. Check product price and the order Total | Any product from the product list | The shopping cart should show 2 of the product and a total that matches the unit price times 2 | Verifies the correct behavior of quantity selection and total price calculation through the product detail view |
| Verify that adding three units of the same product multiplies the product price correctly in the cart | 1. Go to homepage <br> 2. Find any product <br> 3. Click on “View product” button on the product card <br> 4. Enter “3” on “Quantity” <br> 5. Click on “Add to cart” button <br> 6. Click on “View Cart” button <br> 7. Check product price and the order Total | Any product from the product list | The cart should show a quantity of three, and the total amount must be equal to the unit price multiplied by three | Verifies that the multiplication logic continues to work correctly with quantities greater than two |
| Verify that adding two different products from the product list updates the cart total correctly | 1. Go to homepage <br> 2. Find any product <br> 3. Click “Add to cart” <br> 4. Click on “Continue shopping” button <br> 5. Find any product <br> 6. Click “Add to cart” <br> 7. Click on “View Cart” button <br> 8. Click on “Proceed to checkout” <br> 9. Check products prices and the order Total | 2 products from the product list | The cart should list both selected products with a quantity of one each. The total amount displayed should be equal to the sum of the unit prices of the two products | Verifies that the shopping cart correctly calculates the total |
| Verify that adding two different products from the product detail page updates the cart total correctly | 1. Go to homepage <br> 2. Find any product <br> 3. Click on “View product” button on the product card <br> 4. Click on “Add to cart” button <br> 5. Click on “Products” button from the navbar <br> 6. Find another product <br> 7. Click on “View product” button on the product card <br> 8. Click on “Add to cart” button <br> 9. Click on “View Cart” button <br> 10. Click on “Proceed to checkout” <br> 11. Check product prices and the order Total | 2 products from the product list | The cart should list both selected products with a quantity of one each. The total amount displayed should be equal to the sum of the unit prices of the two products | Verifies that the price logic works consistently when items are added via product details section |
| Verify that logging in first and then adding two units of the same product from the product list updates the cart total correctly | 1. Go to homepage <br> 2. Log in with valid credentials <br> 3. Find any product <br> 4. Click “Add to cart” <br> 5. Click on “Continue shopping” button <br> 6. Find any product <br> 7. Click “Add to cart” <br> 8. Click on “View Cart” button <br> 9. Click on “Proceed to checkout” <br> 10. Check products prices and the order Total | Any user account and any product | The cart should show a quantity of two for the product, and the total should be calculated correctly | Verifies that user session context doesn’t interfere with the cart total calculation when using the product list |
| Verify that logging in first and then adding two units of the same product from the product detail page updates the cart total correctly | 1. Go to homepage <br> 2. Log in with valid credentials <br> 3. Find any product <br> 4. Click on “View product” button on the product card <br> 5. Enter “2” on “Quantity” <br> 6. Click on “Add to cart” button <br> 7. Click on “View Cart” button <br> 8. Check product price and the order Total | Any user account and any product | The cart should show a quantity of two for the product, and the total should be calculated correctly | Verifies that user session context does not interfere with the cart total calculation when using the product details |
| Verify that logging in first and then adding two different products from the product list updates the cart total correctly | 1. Go to homepage <br> 2. Log in with valid credentials <br> 3. Find any product <br> 4. Click “Add to cart” <br> 5. Click on “Continue shopping” button <br> 6. Find any product <br> 7. Click “Add to cart” <br> 8. Click on “View Cart” button <br> 9. Click on “Proceed to checkout” <br> 10. Check products prices and the order Total | Any user account and two different products | The cart should list both selected products with a quantity of one each. The total amount displayed should be equal to the sum of the unit prices of the two products | Verifies that user session context does not interfere with the cart total calculation when using the product list for different products |
| Verify that logging in first and then adding two different products from the product detail page updates the cart total correctly | 1. Go to homepage <br> 2. Log in with valid credentials <br> 3. Find any product <br> 4. Click on “View product” button on the product card <br> 5. Click on “Add to cart” button <br> 6. Click on “Products” button from the navbar <br> 7. Find another product <br> 8. Click on “View product” button on the product card <br> 9. Click on “Add to cart” button <br> 10. Click on “View Cart” button <br> 11. Click on “Proceed to checkout” <br> 12. Check product prices and the order Total | Any user account and two different products | The cart should list both selected products with a quantity of one each. The total amount displayed should be equal to the sum of the unit prices of the two products | Verifies that user session context does not interfere with the cart total calculation when using the product details for different products |
| Verify that after adding two different products to the cart, removing one updates the cart total correctly | 1. Go to homepage <br> 2. Find any product <br> 3. Click “Add to cart” <br> 4. Click on “Continue shopping” button <br> 5. Find any product <br> 6. Click “Add to cart” <br> 7. Click on “View Cart” button <br> 8. Click on “Proceed to checkout” <br> 9. Check products prices and the order Total <br> 10. Click on Cart button from the navbar <br> 11. Remove one product <br> 12. Click on “Proceed to checkout” <br> 13. Check products prices and the order Total | 2 products from the product list | After removing one of the two products, the cart should display only the remaining product. The total amount should be updated to reflect the price of the remaining product alone | Verifies that the cart correctly recalculates the total when one item is removed |


## 3. Regression test cases
| Test Case Title | Test Steps | Test Data | Expected Result | Why Included (Scope/Reasoning) |
|-----------------|------------|-----------|------------------|-------------------------------|
| Verify that it is possible to change the quantity of items displayed in the Cart by modifying the quantity selection | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “View Cart” button<br>5. Change the quantity of the product from the cart and add one more item | Any product from the product list | The cart updates to display exactly the number of items corresponding to the selected quantity | To ensure that the quantity selection control affects the cart display correctly |
| Verify that increasing the quantity of a product from the cart updates the total correctly | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “View Cart” button<br>5. Change the quantity of the product from the cart and add one more item | Any product from the product list | The cart total should update to reflect the amount of items selected | Validates quantity update logic inside the cart |
| Verify that decreasing the quantity of a product from the cart updates the total correctly | 1. Go to homepage<br>2. Find any product<br>3. Click on “View product” button on the product card<br>4. Enter “5” on “Quantity”<br>5. Click on “Add to cart” button<br>6. Click on “View Cart” button<br>7. Decrease quantity (e.g. 3 items) | Any product from the product list | The subtotal and cart total should update to reflect the amount of items selected | Validates quantity update logic inside the cart |
| Verify that cart total remains consistent after refreshing the cart page | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “Continue shopping” button<br>5. Click on “View Cart” button<br>6. Refresh the browser | Any product from the product list | Product and correct total remain displayed after reload | Verifies data persistence and frontend stability |
| Verify that cart total remains correct after logging out and logging in again | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “Continue shopping” button<br>5. Click on “View Cart” button<br>6. Log out from page<br>7. Log back in<br>8. Go to Cart | Any product from the product list | Cart contents and total remain unchanged | Verifies session/cart persistence |
| Verify that the Invoice displays the correct total after completing a purchase | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “Continue shopping” button<br>5. Click on “View Cart” button<br>6. Click on Proceed to checkout<br>7. Click on Place Order<br>8. Fill in the form with valid payment details<br>9. Click on Pay and Confirm Order<br>10. Click on Download Invoice<br>11. Open the .txt file and observe the order total | Any product from the product list, payment details | The total amount displayed in the Invoice exactly matches the total displayed on the Review Your Order section | Ensure consistency in the purchase flow |
| Verify that quantity input rejects negative values | 1. Go to homepage<br>2. Find any product<br>3. Click on “View product” button on the product card<br>4. Enter a negative number | Any product | Negative input is rejected and product is not added to the cart | To ensure negative numbers are not accepted in the quantity field |
| Verify that quantity input rejects symbol characters | 1. Go to homepage<br>2. Find any product<br>3. Click on “View product” button on the product card<br>4. Enter a symbol e.g. “.” | Any product | Symbol input is rejected and product is not added to the cart | To ensure symbols are not accepted in the quantity field |
| Verify that quantity input rejects non-numeric text values | 1. Go to homepage<br>2. Find any product<br>3. Click on “View product” button on the product card<br>4. Enter a text value | Any product | Text input is rejected and product is not added to the cart | To ensure text is not accepted in the quantity field |
| Verify that quantity input rejects zero as a valid value | 1. Go to homepage<br>2. Find any product<br>3. Click on “View product” button on the product card<br>4. Enter 0 as the quantity | Any product | Zero input is rejected and product is not added to the cart | To ensure zero is not accepted in the quantity field |
| Verify that adding the same product from different sections results in correct quantity and total | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “Continue shopping” button<br>5. Go to Products on the navbar<br>6. Locate the same product from step 2<br>7. Click on the product card to open product details<br>8. Click on Add to cart<br>9. Click on View cart | Any product | Cart merges quantities and calculates total correctly | Tests if identical items from different flows are merged |
| Verify that removing all products with multiple quantities clears the cart and resets the total | 1. Go to homepage<br>2. Find any product<br>3. Click on “View product” button on the product card<br>4. Enter a number higher than 1 on “Quantity”<br>5. Click on “Add to cart” button<br>6. Click on “Continue shopping” button<br>7. Find another product<br>8. Click on “View product” button on the product card<br>9. Enter a number higher than 1 on “Quantity”<br>10. Click on “Add to cart” button<br>11. Click on “View cart” button<br>12. Remove both items by clicking the “x” for each set of items | 2 products from the product list | Cart becomes empty | Validates complete reset of cart after multiple removals |
| Verify that refreshing the checkout page does not alter product quantities or totals | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “Continue shopping” button<br>5. Click on “View Cart” button<br>6. Click on “Proceed to checkout”<br>7. Refresh the browser | Any product | Quantities and totals remain unchanged | Tests stability of state across checkout reloads |
| Verify that navigating between cart and checkout preserves quantities and totals | 1. Go to homepage<br>2. Find any product<br>3. Click “Add to cart”<br>4. Click on “Continue shopping” button<br>5. Click on “View Cart” button<br>6. Click on “Proceed to checkout”<br>7. Click on “Cart” button to return to cart | Any product | Quantities and totals remain unchanged across pages | Ensures the fix remains consistent across user navigation |

## 4. Bug reports

### [MSB-001] - Cannot modify product quantity from cart

| Field           | Description |
|----------------|-------------|
| **Description** | Users are unable to modify the quantity of a product directly from the cart. To set a new quantity, they must remove the product entirely and add it again with the new amount. |
| **Environment** | Preproduction environment at URL: https://automationexercise.com/  <br> Chrome web browser <br> OS: Windows 10 <br> Stable network connection |
| **Reported By** | Micaela Serra |
| **Preconditions** | Have at least one product on the product list |
| **Steps to Reproduce** | 1. Go to https://automationexercise.com  <br> 2. Find any product  <br> 3. Click on the “View product” button  <br> 4. Enter a number higher than 1 in the “Quantity” input field (e.g., 5) <br> 5. Click on “Add to cart” <br> 6. Click on “View Cart” <br> 7. Try to decrease the quantity (e.g., from 5 to 3) |
| **Expected Result** | The cart should allow modifying the product quantity and the prices should be updated accordingly. |
| **Actual Result** | There is no available option to change the quantity from the cart. Users are forced to delete the product and add it again. |
| **Severity** | Medium |
| **Priority** | High |
| **Why** | This affects a common e-commerce flow and adds unnecessary steps to the user experience. |
| **Workaround** | Remove the product and re-add it with the desired quantity via the product detail page. |
| **Status** | New |

---

### [MSB-002] - Quantity input accepts negative or zero values and allows checkout with invalid total

| Field           | Description |
|----------------|-------------|
| **Description** | The quantity input field lacks validation, allowing zero or negative values. This results in invalid totals at checkout and invoices. |
| **Environment** | Production environment at URL: https://automationexercise.com/ <br> Chrome web browser <br> OS: Windows 10 <br> Stable network connection |
| **Reported By** | Micaela Serra |
| **Preconditions** | Have at least one product on the product list. |
| **Steps to Reproduce** | **Scenario 1** <br> 1. Go to the site  <br> 2. View any product  <br> 3. Enter `0` in quantity <br> 4. Add to cart <br> 5. View cart <br> 6. Proceed to checkout <br> 7. Download invoice <br><br> **Scenario 2** <br> 1. Go to the site <br> 2. View any product <br> 3. Enter `-4` in quantity <br> 4. Add to cart <br> 5. View cart <br> 6. Proceed to checkout <br> 7. Download invoice |
| **Expected Result** | Scenario 1: Reject quantity 0. <br> Scenario 2: Block negative quantities. No checkout should proceed with invalid totals. |
| **Actual Result** | Both cases allow invalid entries and result in $0 totals in the final invoice. |
| **Severity** | High |
| **Priority** | High |
| **Why** | Users can generate invalid orders, leading to confusion and incorrect data. |
| **Workaround** | No system validation. Users must manually avoid entering invalid values. |
| **Attachments** | Scenario1.mp4, Scenario2.mp4 |
| **Status** | New |

---

### [MSB-003] - Footer copyright year outdated

| Field           | Description |
|----------------|-------------|
| **Description** | The footer shows "© 2021", which is outdated and may give a bad impression. |
| **Environment** | Production environment at URL: https://automationexercise.com/ <br> Chrome web browser <br> OS: Windows 10 <br> Stable network connection |
| **Reported By** | Micaela Serra |
| **Preconditions** | N/A |
| **Steps to Reproduce** | 1. Go to https://automationexercise.com/ <br> 2. Scroll down to footer <br> 3. Observe the copyright |
| **Expected Result** | The footer should show the current year (e.g., 2025). |
| **Actual Result** | Footer shows "2021", indicating outdated content. |
| **Severity** | Low |
| **Priority** | Low |
| **Why** | Outdated information reduces trust and suggests the site is not maintained. |
| **Workaround** | None. Static content needs manual update. |
| **Status** | New |

---

### [MSB-004] - Inconsistent product card sizes affect page layout

| Field           | Description |
|----------------|-------------|
| **Description** | Product cards have inconsistent sizes, causing layout misalignment and poor visual appeal. |
| **Environment** | Production environment at URL: https://automationexercise.com/ <br> Chrome web browser <br> OS: Windows 10 <br> Stable network connection |
| **Reported By** | Micaela Serra |
| **Preconditions** | N/A |
| **Steps to Reproduce** | 1. Go to https://automationexercise.com <br> 2. Navigate to any product listing page <br> 3. Observe card sizes and alignment |
| **Expected Result** | Product cards should have consistent size and layout. |
| **Actual Result** | Cards vary in size, leading to misalignment and disorganized UI. |
| **Severity** | Medium |
| **Priority** | Medium |
| **Why** | Affects the professionalism of the site and user experience. |
| **Workaround** | None |
| **Status** | New |
