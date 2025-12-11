# Expense Tracker React – Budget & Dashboard Enhancement

Final Group Project – Software Project Management  
Open Source Enhancement – Expense Tracker (React)

Repository: https://github.com/Rahul26240/expense-tracker-react

---

## 1. Project Overview

This project enhances an existing open-source **Expense Tracker React** application by adding a complete **Budget Management & Dashboard feature set**.

The enhancement focuses on:

- Defining and managing a **monthly budget**
- Calculating and showing **remaining budget** in real time
- A **dashboard summary** (budget, spending, remaining)
- A **spending vs budget chart**
- A centralized **validation system**
- **Testing & QA** with clear traceability
- Organized **GitHub Project Management** using Epics, Issues, Relationships, and Milestones

The goal is not only to add functionality, but also to demonstrate **good project management practices**: clear requirements, assumptions, validation plan, issue breakdown, epics, milestones, and production readiness.

---

## 2. Base Application (Open Source Project)

**Base Project:** Expense Tracker built with React  
**Technology Stack:**

- React (Functional Components, Hooks)
- Context API for global state
- JavaScript / JSX
- CSS for styling
- Local storage for persistence (after enhancement)

The original app mainly handled **tracking expenses**. The enhancement builds on top of it to add **budget awareness and richer visualization**.

---

## 3. Enhancement Summary

### 3.1 Enhancement Goals

The enhancement introduces a **Budget Module** and **Dashboard Enhancements**:

1. Allow users to **define and update a monthly budget**.
2. Calculate **remaining budget** based on total spending.
3. Provide a **dashboard summary view** for:
   - Monthly Budget
   - Total Spending
   - Remaining Budget
   - Status indicator (under / near / over budget)
4. Provide a **chart** showing **Spending vs Budget**.
5. Add **validation** for budget and transaction inputs.
6. Add **local storage persistence** for budget and transactions.
7. Improve **UI styling and responsiveness**.
8. Implement a **testing & QA process** with issues and a test plan.

---

## 4. Requirements

### 4.1 Functional Requirements

**FR-1: Define Monthly Budget**  
- User can enter a numeric monthly budget.
- Budget cannot be negative or empty.
- Budget is stored in state and later persisted.

**FR-2: Update Monthly Budget**  
- User can modify the existing budget.
- Remaining budget recalculates immediately.
- Dashboard and chart reflect updated values.

**FR-3: Remaining Budget Calculation**  
- System calculates:
  - `remainingBudget = monthlyBudget - totalSpending`
- Updates whenever:
  - Budget changes
  - Transactions are added/edited/deleted

**FR-4: Dashboard Summary**  
- Dashboard displays:
  - Monthly Budget
  - Total Spending
  - Remaining Budget
  - Status indicator (green/yellow/red)
- Dashboard updates automatically on state changes.

**FR-5: Spending vs Budget Chart**  
- Chart compares:
  - Total Spending vs Monthly Budget
- Auto-updates on budget or transaction changes.
- Shows clear visual difference.

**FR-6: Validation**  
- Budget input:
  - Required, numeric, ≥ 0
- Transaction:
  - Amount required, numeric, > 0
  - Description required
- Invalid input shows clear error messages.

**FR-7: Persistence**  
- Budget and transaction data are stored in local storage.
- Data is restored when user revisits the app.

**FR-8: Testing & QA**  
- A test plan is defined.
- Critical paths (budget, remaining, dashboard) tested.
- Bugs are tracked and retested via GitHub issues.

---

### 4.2 Non-Functional Requirements

- **Usability:** UI must be simple and intuitive.
- **Performance:** Calculations and UI updates happen instantly (no noticeable lag).
- **Reliability:** No invalid data should enter the system.
- **Maintainability:** Code separated into reusable components, context, and services.
- **Responsiveness:** Dashboard works on desktop and mobile screen sizes.

---

## 5. Assumptions & Constraints

### 5.1 Assumptions

- Single user using the application in one browser (no multi-user accounts).
- Budget is defined **per month** (no yearly or weekly budgeting yet).
- Time zone and currency specifics are not critical for this assignment.
- Users are comfortable entering amounts manually.

### 5.2 Constraints

- Enhancement must use the existing **React** codebase.
- Must align with the course **Final Project** requirements.
- Must be managed fully in **GitHub Projects** (Issues, Epics, Milestones).
- No backend server or database – persistence via **localStorage** only.

### 5.3 Validation Plan (High-Level)

To validate assumptions and requirements:

- Manual testing using realistic usage scenarios.
- Traceability from **requirements → issues → implementation → tests**.
- Visual verification of UI and charts.
- Reviewing GitHub project board and relationships to ensure workflows are covered.

---

## 6. System Design & Diagrams

> Note: Diagrams are stored in `/docs` (filenames may be adjusted to match actual uploads).

- `/docs/architecture-diagram.png` – High-level architecture (Contexts + Components).
- `/docs/uml-class-diagram.png` – UML for BudgetContext, TransactionContext, and key components.
- `/docs/component-hierarchy.png` – React component tree for Dashboard.
- `/docs/dashboard-wireframes.png` – Wireframes for desktop and mobile dashboard.

### 6.1 Architecture Overview

**Key pieces:**

- `BudgetContext`  
  - Holds `monthlyBudget`, `remainingBudget`, and update functions.
- `TransactionContext`  
  - Holds expense list and `totalSpending`.
- `DashboardSummary`  
  - Displays Budget / Spent / Remaining + status.
- `BudgetInput`  
  - UI for setting/updating budget.
- `BudgetSpendingChart`  
  - Visual comparison of budget vs spending.
- `ValidationService`  
  - Shared validation logic for all inputs.

Data flow:

1. User sets/updates budget via `BudgetInput`.
2. `BudgetContext` stores budget and calculates remaining.
3. Transactions trigger `totalSpending` in `TransactionContext`.
4. Dashboard and chart subscribe to both contexts and update reactively.

---

## 7. Project Management Structure (GitHub)

The project uses **GitHub Issues + Epics + Milestones + Relationships** to show proper project management.

### 7.1 Epics (Parent Issues)

The following Epics are created as **parent issues**:

1. **EPIC: Monthly Budget Feature (Define, Update & Manage Budget)**  
2. **EPIC: Dashboard Summary & Financial Overview**  
3. **EPIC: Spending vs Budget Chart Feature**  
4. **EPIC: Input Validation System**  
5. **EPIC: Testing & QA for Budget Module**  
6. **EPIC: Requirements, Assumptions, Diagrams & Planning**

Each Epic has multiple **sub-issues** attached via the GitHub “Relationships → Parent issue” panel.

### 7.2 Example Epic → Issues Mapping

**EPIC: Monthly Budget Feature**  
Sub-issues include (issue numbers may vary):

- #1 – Define Monthly Budget (user story)
- #2 – UI for Budget Input
- #3 – Remaining Budget Calculation
- #15 – Implement BudgetContext
- #16 – BudgetInput Component
- #17 – Budget Update Logic
- #24 – Budget Validation
- #27 – Local Storage for Budget

**EPIC: Dashboard Summary & Financial Overview**

- #4 – Dashboard Summary User Story
- #20 – DashboardSummary Component
- #26 – Wire Dashboard to Live Data
- #28 – Dashboard UI Styling

…and similarly for Chart, Validation, Testing, and Requirements Epics.

### 7.3 Blocking / Blocked-By Relationships

Some key dependency relationships:

- `BudgetContext` (e.g., #15)  
  **blocks**:
  - BudgetInput (#16)
  - Remaining Calculation (#19)
  - DashboardSummary (#20)

- `ValidationService` (#23)  
  **blocks**:
  - Budget Validation (#24)
  - Transaction Validation (#25)

- Chart Library Integration (#21)  
  **blocks**:
  - Auto-update chart (#22)

- Test Plan (#29)  
  **blocks**:
  - Final Testing & Bug Retesting (#8, #30)

This models a **critical path** from requirements → core logic → UI → testing.

### 7.4 Milestones

Milestones are used like phases:

- **Milestone 1 – Requirements & Design (Month 1 of 3)**
  - Requirements, scope, assumptions, diagrams.
- **Milestone 2 – Development & Integration (Month 2 of 3)**
  - Contexts, components, dashboard, chart, validation, persistence.
- **Milestone 3 – Testing & Finalization (Month 3 of 3)**
  - Test plan, execution, bug fixes, final documentation.

All issues are assigned to **one of the milestones**, showing clear planning and timeboxing.

---

## 8. Implementation Overview

### 8.1 Frontend (React)

- Built using functional components and hooks (`useState`, `useContext`, `useEffect`).
- New components:
  - `BudgetInput`
  - `DashboardSummary`
  - `BudgetSpendingChart`
- Styling:
  - Consistent with existing app.
  - Improved spacing, layout, and responsiveness for dashboard.

### 8.2 State Management (Context)

- **BudgetContext**:
  - `monthlyBudget`
  - `remainingBudget`
  - `setBudget()`, `updateBudget()`, `calculateRemaining()`
- **TransactionContext**:
  - List of transactions
  - `totalSpending` calculation for current period

### 8.3 Persistence

- `localStorage` used to store:
  - `monthlyBudget`
  - Transactions
- On app load:
  - Data is read from `localStorage` (if available)
  - Contexts hydrate from stored values

---

## 9. Validation & Error Handling

Validation is centralized in a **ValidationService** module:

- `validateBudget(amount)`  
- `validateAmount(amount)`  
- `validateDescription(text)`  

Used by:

- `BudgetInput` (budget form)
- Transaction form

**Error Handling:**

- Invalid values prevent form submission.
- Error messages displayed inline under input.
- No invalid data is stored in context or local storage.

---

## 10. Testing & QA

Testing is managed via GitHub issues and a test plan.

### 10.1 Test Plan (Issue #29)

The test plan covers:

- Budget creation & update
- Remaining budget calculation
- Dashboard updates
- Chart behavior
- Validation behavior
- Responsiveness on different screen sizes
- Regression tests to ensure existing expense features still work

### 10.2 Final Testing & Bug Fixes (Issues #8, #30)

- Execute full test plan.
- Log defects as GitHub issues (where applicable).
- Retest after fixes.
- Close issues after verification.
- Ensure the application is **production-ready** at the end.

---

## 11. Requirements Traceability (Sample)

| Requirement (FR)                    | Issue(s)                    | Epic                          |
|------------------------------------|-----------------------------|-------------------------------|
| FR-1 Define Monthly Budget         | #1, #2, #15, #16            | EPIC: Monthly Budget Feature  |
| FR-3 Remaining Budget Calculation  | #3, #18, #19                | EPIC: Monthly Budget Feature  |
| FR-4 Dashboard Summary             | #4, #20, #26, #28           | EPIC: Dashboard Summary       |
| FR-5 Spending vs Budget Chart      | #5, #21, #22                | EPIC: Chart Feature           |
| FR-6 Validation                    | #6, #23, #24, #25           | EPIC: Validation System       |
| FR-8 Testing & QA                  | #8, #29, #30                | EPIC: Testing & QA            |

This traceability shows that each requirement is implemented and testable via mapped GitHub issues.

---

## 12. How to Run the Project

```bash
# Clone the repository
git clone https://github.com/Rahul26240/expense-tracker-react.git

cd expense-tracker-react

# Install dependencies
npm install

# Start the development server
npm start


