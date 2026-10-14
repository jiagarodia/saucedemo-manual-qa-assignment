# Swag Labs QA Assignment

## Overview

This assignment was completed using the pure QA path. The focus was on manual testing, exploratory analysis, risk assessment, and defect documentation. Automation steps were intentionally excluded as per the pure QA requirement.

---

## 1. Test Plan

### 1.1 Scope

The testing scope includes:

- User login and authentication
- Product listing and sorting
- Cart operations
- Checkout flow
- Negative and error conditions
- Basic cross-browser and responsive UI checks

### 1.2 Types of Testing

- Functional Testing
- UI/UX Testing
- Negative Testing
- Boundary and Edge-Case Testing
- Exploratory Testing
- Cross-Browser Considerations

### 1.3 Test Environment

- Browsers: Chrome, Edge, Firefox
- Devices: Desktop and mobile emulation
- Resolutions: 1280x720, 1440x900, and mobile viewports
- OS: Windows and browser-based testing environment

### 1.4 Test Data

Users provided by the application:

- standard_user
- locked_out_user
- problem_user
- performance_glitch_user
- error_user
- visual_user

Common password:

- secret_sauce

### 1.5 Detailed Test Cases

| ID | Test Case | Steps | Expected Result | Priority |
| --- | --- | --- | --- | --- |
| TC-01 | Login with valid user | Open the website, enter standard_user and secret_sauce, then click Login | User is successfully logged in and redirected to the inventory page | High |
| TC-02 | Login with locked-out user | Enter locked_out_user and secret_sauce, then click Login | User is denied access and the account lock error is displayed | High |
| TC-03 | Product sorting | Open the inventory page and change sort to Price (low to high) | Products are displayed in correct ascending price order | High |
| TC-04 | Add item to cart | Select any product and click Add to cart | The cart badge updates and the item is added successfully | High |
| TC-05 | Remove item from cart | Add a product, open cart, and remove it | The item is removed and the cart count is updated correctly | High |
| TC-06 | Checkout with valid details | Add an item, proceed to checkout, fill in name, last name, postal code, continue, and finish order | Order is completed successfully and confirmation is shown | Critical |
| TC-07 | Empty cart checkout attempt | Try to proceed to checkout with no item in cart | The user is prevented from continuing and guided to add products first | Medium |
| TC-08 | Invalid checkout input | Leave required fields blank or enter invalid data | The form blocks submission and prompts the user to correct data | High |
| TC-09 | Refresh after cart operations | Add product, refresh page, and observe cart state | The app state remains consistent and predictable | Medium |
| TC-10 | Navigation sanity check | Open the menu and click About/other navigation links | Links work correctly and do not lead to broken pages | Medium |

### 1.6 Risk Assessment

Highest-risk areas identified during testing:

- Authentication and authorization flow
- Cart state management
- Checkout validation
- Static asset loading and broken navigation
- UI stability across device/browser conditions

Potential impact areas:

- Incorrect user access control
- Lost trust due to broken navigation or missing images
- Incorrect cart amounts or stale state
- Failed purchase process due to validation defects

---

## 2. Bug Reports

### Bug 1: About Link Redirects to Broken Page

- ID: BUG-01
- Severity: Medium
- Summary: The sidebar About link directs the user to a 404 page instead of a valid destination.
- Steps to Reproduce:
  1. Log in to the application.
  2. Open the side menu.
  3. Click About.
- Expected Result: The user should be taken to a valid Sauce Labs page or a functioning About page.
- Actual Result: The browser navigates to a broken URL such as https://saucelabs.com/error/404.
- Impact: Broken navigation reduces user trust and makes the website seem unreliable.

### Bug 2: Product Images Fail to Load for Some Users

- ID: BUG-02
- Severity: High
- Summary: Some product images and other static resources fail to load, causing the storefront to appear broken or incomplete.
- Steps to Reproduce:
  1. Log in with problem_user.
  2. Open the inventory page.
  3. Observe product images and browser console errors.
- Expected Result: All product images should load normally.
- Actual Result: Console shows failed resource requests with 401 Unauthorized responses and some images do not render.
- Impact: The visual experience is poor and users may doubt the website's credibility.

### Bug 3: Reset App State Does Not Fully Restore the Cart State

- ID: BUG-03
- Severity: High
- Summary: Reset App State does not always fully restore the cart to a clean default state.
- Steps to Reproduce:
  1. Add one or more products to the cart.
  2. Open the side menu.
  3. Click Reset App State.
- Expected Result: Cart count and product state should reset completely.
- Actual Result: Cart count and item state may remain inconsistent after reset.
- Impact: Users may be confused by stale cart data during checkout or browsing.

### Bug 4: Checkout Validation Is Not Consistently Enforced

- ID: BUG-04
- Severity: High
- Summary: The checkout form allows invalid or incomplete data handling in some conditions.
- Steps to Reproduce:
  1. Add an item to the cart.
  2. Start checkout.
  3. Leave fields empty or enter incomplete values.
- Expected Result: The system should block invalid submission until mandatory data is entered correctly.
- Actual Result: In some cases, the flow continues without consistent validation.
- Impact: This can lead to incorrect orders or user frustration during purchase.

### Bug 5: Product Sorting Behavior Is Not Fully Trustworthy

- ID: BUG-05
- Severity: Medium
- Summary: Product sorting does not always appear consistent when switching between sort modes.
- Steps to Reproduce:
  1. Open the products list.
  2. Change sorting between Name and Price options.
  3. Compare the final order with expected logic.
- Expected Result: Products should always follow the selected sort rule correctly.
- Actual Result: Ordering may appear inconsistent or not match expectations under some conditions.
- Impact: Users may struggle to compare products or find items efficiently.

### Bug 6: Authentication Error Handling Is Inconsistent Across Users

- ID: BUG-06
- Severity: Medium
- Summary: Special test users show inconsistent authentication behavior and error handling.
- Steps to Reproduce:
  1. Try logging in with different provided usernames.
  2. Observe the results and error messaging.
- Expected Result: Each user should receive a clear and accurate access result.
- Actual Result: Some users produce inconsistent or misleading responses.
- Impact: This weakens confidence in the login system and creates confusion for users and testers.

---

## 3. Final QA Conclusion

The Swag Labs website is a strong candidate for manual QA testing because it covers multiple user journeys, including login, inventory, cart, and checkout. The most critical risks are centered around authentication, cart integrity, checkout flow, and navigation reliability. Through exploratory testing, several issues were identified that affect the overall product quality and user trust.

This document is suitable for direct submission in the pure QA path and intentionally does not include automation work, as required by the assignment.
