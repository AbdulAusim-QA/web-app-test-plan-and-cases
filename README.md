# Web App Test Plan and Cases

## Overview
This repository contains a QA testing project where I tested a sample web
application end to end and documented the work the same way I would on a real
QA project.

The intent of this repository is to show **how I think about testing**, not
just the final outputs. It covers planning, scenario design, detailed test
cases, and how issues are documented and communicated.

The focus is on quality, risk awareness, and clarity rather than test volume.

---

## Application Under Test
https://www.saucedemo.com

---

## What I Did in This Project

While working on this project, I followed a structured and practical testing
approach:

- Reviewed the application to understand core user workflows and potential
  risk areas
- Defined a **test strategy** to clarify scope, priorities, and the overall
  testing approach
- Created **test scenarios** to describe what should be tested based on real
  user behavior
- Designed **detailed test cases** for each major module, written in a way
  that can be executed and repeated
- Included **negative and edge-case scenarios** where appropriate
- Considered **non-functional aspects** such as usability, session handling,
  and basic security behavior
- Documented issues using **JIRA-style tickets** to demonstrate defect
  tracking and communication practices

The goal was to reflect how testing is planned, executed, and communicated
within real QA teams.

---

## Testing Scope

The following areas were covered:

- Authentication (login, logout, input validation)
- Session handling and access control
- Product listing (inventory)
- Product Detail Page (PDP)
- Cart functionality
- Checkout flow
- Basic security and negative scenarios

---

## Testing Types Applied

- Smoke Testing  
- Functional Testing  
- Regression Testing  
- Usability Testing  
- Basic Security Checks  

---

## Repository Structure

The repository is organized for easy review:

- **Test_Strategy/**  
  Contains the test strategy outlining scope, approach, risks, and entry/exit
  criteria.

- **Test_Scenarios/**  
  High-level test scenarios describing what was tested and why, based on user
  workflows and risk areas.

- **Test_Cases/**  
  Detailed test cases written in Excel and organized by module, including:
  - Authentication
  - Session management
  - Inventory
  - Product Detail Page (PDP)
  - Cart
  - Checkout
  - Security

- **Jira_Tickets/**  
  Sample JIRA-style defect tickets created to show how issues were logged,
  prioritized, and communicated during testing.

---

## Defect Tracking Approach

Issues identified during testing were documented using a JIRA-style format.
Each ticket includes:

- Clear steps to reproduce
- Expected versus actual behavior
- Severity and priority assessment
- Impact explanation

These examples are included to demonstrate my approach to defect tracking and
communication. They are not taken from a live JIRA system.

---

## Key Takeaways

- Used a **risk-based and scenario-driven** approach to testing
- Designed test cases aligned with real user workflows
- Focused on clarity and usefulness in defect documentation
- Organized testing artifacts so reviewers can quickly understand what was
  tested and how

