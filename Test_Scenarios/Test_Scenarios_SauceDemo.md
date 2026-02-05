# Test Scenarios – SauceDemo

## Goal
Provide scenario-based coverage of key user workflows and common failure modes for authentication, product browsing, cart management, and checkout. Scenarios emphasize user impact, data integrity, session behavior, and clear system feedback.

---

## 1) Authentication & Access Control

### TS_AUTH_01 – Successful login and landing behavior (High)
Validate that a user can authenticate with valid credentials and is routed to the expected landing page with the correct page elements visible (inventory list, navigation controls, cart icon). Confirm there is no unexpected banner or stale error message from prior attempts. Verify the URL and page title/heading represent the logged-in state and that the login form is no longer accessible via normal navigation.

### TS_AUTH_02 – Failed login with incorrect credentials and clear user feedback (High)
Validate system behavior when login attempts fail due to incorrect username and/or password. Confirm an error message is displayed, is understandable, and does not expose sensitive details. Verify input fields remain editable, the user is not logged in, and the application does not partially load authenticated content. Check that repeated invalid attempts behave consistently and do not degrade UI layout or responsiveness.

### TS_AUTH_03 – Login validation with missing inputs (High)
Validate application response when the user attempts to log in with required fields missing (blank username, blank password, both blank). Confirm the application blocks authentication, displays an appropriate validation message, and provides clear guidance. Verify focus/interaction remains on the login screen and no authenticated routes become available.

### TS_AUTH_04 – Locked/edge user handling and consistent messaging (Medium)
If using any provided “locked” user credentials (when applicable), validate that the application prevents access and displays a clear message. Confirm behavior is consistent across attempts and that the user cannot proceed to inventory pages through direct URLs. Ensure the message is presented consistently (format, placement, no overlap) and does not break layout.

---

## 2) Session Handling & Logout

### TS_SESS_01 – Logout workflow and post-logout access restriction (High)
Validate that a logged-in user can log out through the application navigation menu. Confirm the user returns to the login screen, that authenticated pages are no longer accessible, and that any session-dependent UI (cart badge, inventory content) is cleared from view. Attempt to use browser back/forward navigation and confirm the user cannot regain access without logging in again.

### TS_SESS_02 – Direct URL access control for authenticated pages (High)
Validate that protected routes require authentication (e.g., inventory, cart, checkout pages). Attempt to open authenticated URLs in a new tab/window when not logged in and confirm the application redirects to the login page or blocks access with appropriate handling. Confirm there is no leakage of user-specific state (cart badge count, item listings) prior to authentication.

### TS_SESS_03 – Stability during normal navigation within an active session (Medium)
Validate that an active session remains stable while the user navigates between inventory, product detail, cart, and checkout pages. Confirm there is no unexpected logout, session reset, or loss of state (cart contents) during normal use. Verify navigation controls behave consistently across pages (menu, cart icon, back navigation patterns).

---

## 3) Inventory (Product Listing) Page

### TS_INV_01 – Inventory page content integrity and completeness (High)
Validate that inventory loads reliably after login and displays the expected product list. Confirm each product card shows key information (name, price, image, description snippet if applicable) and contains a clear action to add/remove items from cart. Check for visual consistency (alignment, spacing, readable text) and ensure no missing images or broken UI elements.

### TS_INV_02 – Inventory sorting behavior and user expectation (Medium)
Validate that sorting options (e.g., name A–Z/Z–A, price low–high/high–low) reorder products correctly and consistently. Confirm sorting does not remove items, duplicate items, or alter product details (price/name mismatch). Verify the selected sort option remains selected during navigation and returns as expected when moving between pages.

### TS_INV_03 – Product selection and navigation to product detail (Medium)
Validate that selecting a product from the inventory opens a product detail view with correct product data. Confirm the detail page matches the item clicked (name, price, description, image) and provides a clear way to return to inventory. Verify the back navigation does not lose cart state or change the inventory list unexpectedly.

---

## 4) Product Detail Page

### TS_PDP_01 – Add/remove from cart from product detail (High)
Validate that the user can add an item to the cart from the product detail page and that the cart badge updates appropriately. Confirm removing the item reverts the action state and the cart badge count decreases accordingly. Navigate away and return to the product detail page to confirm the add/remove state remains consistent with the cart.

### TS_PDP_02 – Product detail content consistency and non-editable fields (Medium)
Validate that product detail fields are read-only and presented consistently. Confirm there are no truncation issues that hide essential info, and the image renders properly. Verify that returning to inventory preserves the user’s context reasonably (does not unexpectedly reset sorting or lose scroll position, where applicable).

---

## 5) Cart (Basket) Management

### TS_CART_01 – Add single item to cart and verify cart state (High)
Validate adding a single item from inventory results in correct cart state. Confirm the cart badge increments, the cart page shows the correct item, and the item’s displayed name/price matches inventory. Verify removing the item from either inventory or cart updates both views consistently.

### TS_CART_02 – Add multiple items and verify accuracy and completeness (High)
Validate the user can add multiple items (2+), navigate to cart, and confirm all selected items appear exactly once, with correct pricing and details. Verify the cart badge count equals the number of items added. Remove one item and confirm only that item is removed and the badge count updates correctly.

### TS_CART_03 – Cart UI actions and navigation controls (Medium)
Validate cart page actions such as “Continue Shopping” and “Checkout” behave correctly. Confirm “Continue Shopping” returns to inventory without losing cart contents. Confirm the cart is accessible from inventory and product detail pages consistently, and that navigation does not cause duplicate items or inconsistent badge counts.

---

## 6) Checkout – User Information Step

### TS_CO_01 – Checkout initiation and required field validation (High)
Validate that checkout can be initiated from the cart when at least one item exists. Confirm the user information form enforces required fields (first name, last name, postal code). Attempt submissions with missing fields and verify an error is shown clearly and does not proceed to the next step. Confirm corrected inputs allow checkout to continue.

### TS_CO_02 – Checkout data handling and user feedback quality (Medium)
Validate that error messages are actionable and positioned consistently without breaking layout. Confirm user-entered data remains in fields after validation errors (unless expected otherwise). Verify that the user can cancel checkout or navigate back without losing cart contents unexpectedly.

---

## 7) Checkout – Overview & Completion

### TS_CO_03 – Checkout overview accuracy (High)
Validate the overview page displays the correct item list, quantities (if applicable), and prices for items in cart. Confirm the subtotal reflects the sum of item prices and that any additional totals (tax/total) are computed and displayed consistently. Ensure values are not negative, duplicated, or mismatched between item list and totals.

### TS_CO_04 – Order completion and confirmation state (High)
Validate that completing checkout results in an order confirmation page with a clear success indicator. Confirm the application does not show stale cart contents as “pending” after completion. Verify the user can return to inventory after completion and confirm the cart is cleared (badge reset) and add/remove states return to baseline.

---

## 8) Error Handling & Usability

### TS_UX_01 – Error visibility and layout stability (Medium)
Validate that error messages (login/checkout) remain visible, readable, and do not overlap input fields or buttons. Confirm errors can be dismissed or corrected without requiring a page refresh. Verify that the UI remains stable across multiple errors and that controls remain clickable and aligned.

### TS_UX_02 – Consistent labels and state changes for primary actions (Medium)
Validate that primary actions such as “Add to cart” / “Remove” reflect correct state transitions and are consistent across inventory and product detail views. Confirm state changes are immediate and consistent with cart badge count and cart page contents.

---

## 9) Basic Security & Data Integrity Checks

### TS_SEC_01 – Session invalidation and protected navigation (High)
Validate that after logout the session is invalidated and protected pages cannot be accessed via URL, browser history, or opening in a new tab. Confirm that no user-specific state remains visible (cart badge, inventory content) without authentication.

### TS_DATA_01 – Price and item identity consistency across pages (High)
Validate that product identity (name/price) remains consistent across inventory, product detail, cart, and checkout overview. Confirm there are no mismatches such as wrong price shown on cart vs inventory, or wrong item details shown after navigation.


