# SauceDemo-Cypress-UI-Automation-Project

## Overview
This project automates end-to-end UI testing for the [SauceDemo](https://www.saucedemo.com/) website using the Cypress testing framework.  
It validates key user flows such as login, product navigation, add-to-cart, and logout functionalities for both positive and negative scenarios.  

The goal is to demonstrate Cypress basics, Page Object Model (POM) implementation, and reusable custom commands.

---

## Learning Objectives
Through this project, you will learn to:
- Implement UI test automation using Cypress.  
- Structure tests using the Page Object Model (POM).  
- Reuse code efficiently via custom Cypress commands.  
- Handle both positive and negative test scenarios.  

---

## Tools and Technologies
- **Framework:** Cypress  
- **Language:** JavaScript  
- **IDE:** Visual Studio Code  
- **Website:** [SauceDemo.com](https://www.saucedemo.com)

---

## Project Structure
cypress/
│
├── e2e/
│ ├── b_loginFailure.spec.cy.js
│ ├── c_loginSuccess.spec.cy.js
│ ├── e_add_to_cart_fail.cy.js
│ ├── f_add_to_cart_pass.cy.js
│ ├── logout_fail.cy.js
│ ├── logout_pass.cy.js
│
├── pages/
│ ├── loginPage.js
│ ├── homePage.js
│ ├── cartPage.js
│
├── support/
│ ├── commands.js
│ ├── e2e.js
│
└── cypress.config.js

---

## Page Object Model (POM)
Each page has its own class that defines UI elements and actions.

- **loginPage.js** – Handles login form interactions  
- **homePage.js** – Manages homepage actions and logout  
- **cartPage.js** – Handles add/remove item actions  

This approach improves readability, maintainability, and scalability of tests.

---

## Custom Commands
Custom commands are defined in `commands.js` for reusable actions.

```javascript
Cypress.Commands.add('login', (username, password) => {
  cy.visit('https://www.saucedemo.com/');
  cy.get('#user-name').type(username);
  cy.get('#password').type(password);
  cy.get('#login-button').click();
});

Use this reusable command in any test:

cy.login('standard_user', 'secret_sauce');

Test Scenarios Implemented:

Test File	Description	Expected Result:
1. b_loginFailure.spec.cy.js:	Login with invalid credentials	Error message displayed
2. c_loginSuccess.spec.cy.js:	Login with valid credentials	Redirects to Products page
3. e_add_to_cart_fail.cy.js"	Attempt to add product without login	Fails as expected
4. f_add_to_cart_pass.cy.js:	Add item to cart successfully	Cart item visible
5. logout_fail.cy.js:	Attempt to logout without login	Fails as expected
6. logout_pass.cy.js:	Successful logout after login	Redirects to login page
---

Test Execution Summary:
   Spec File	                Tests	 Passed	  Failed	   Duration
1. b_loginFailure.spec.cy.js	  1	      1      	0	      00:06
2. c_loginSuccess.spec.cy.js	  1      	1	      0	      00:04
3. e_add_to_cart_fail.cy.js	    1	      0	      1	      00:01
4. f_add_to_cart_pass.cy.js	    1	      1	      0	      00:06
5. logout_fail.cy.js	          1	      0	      1	      00:07
6. logout_pass.cy.js	          1	      1	      0	      00:05

Total Tests: 6
Passed: 4
Failed: 2
Pass Rate: 67%

The failing tests represent intentional negative cases for validation.

#How to Run the Project
Clone the Repository
git clone <your-repo-link>
cd <project-folder>

1.Install Dependencies :npm install
2.Open Cypress :npx cypress open
3.Run Tests
4.Select E2E Testing.
5.Choose a browser (Chrome or Electron).
6.Run all .cy.js files to execute tests.

