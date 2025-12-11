# Expense Tracker React – Budget Feature Enhancement

> Software Engineering Principles – Final Group Project  
> Group 2 – Expense Tracker React

**Conestoga College – Software Engineering Principles**

**Team**

- Tarun Sarikopula – 9036541  
- Rahul Jadhav – 9002088  
- Mekala Dora Babu – 9028294  

---

## 1. Project Overview

The original **Expense Tracker React** application allowed users to:

- Add income and expense transactions  
- Categorize transactions  
- View a list of past transactions  
- See a simple summary of totals

However, it **did not support budgeting**. Users could not define a monthly budget, track remaining balance, or visually compare spending against a plan.

This project implements a **Budget Feature Enhancement** that turns the app into a simple budgeting assistant. The enhancement adds:

- Monthly budget entry and updates  
- Automatic remaining budget calculation  
- A dashboard summary with status indicators  
- A spending vs. budget chart  
- Centralized validation for all inputs  
- LocalStorage-based persistence  

The goal of the project is not just coding, but also demonstrating **good software engineering and project management practices** using GitHub Projects, issues, milestones, diagrams, and documentation.

---

## 2. Key Features

### Budgeting

- Set a **monthly budget** using a dedicated input field.  
- Update the budget at any time (e.g., if plans change).  
- Budget is validated (numeric, positive, non-empty) before saving.

### Remaining Budget Calculation

- Automatically calculates:
  - Total spending for the month  
  - Remaining budget = `Budget – Total Spending`  
- Tracks financial status with thresholds:
  - **Healthy**: remaining > 50%  
  - **Warning**: 10% – 50%  
  - **Critical**: < 10% or over budget  

### Dashboard Summary

- Central summary panel shows:
  - Monthly Budget  
  - Total Spending  
  - Remaining Budget  
  - Color-coded status indicator (Green / Yellow / Red)  
- Values update **in real time** when budget or transactions change.

### Spending vs Budget Chart

- Interactive chart (e.g., using **Recharts**) to compare:
  - Budget vs. total spending  
- Reacts to changes in:
  - Budget  
  - Transaction list  
- Shows a friendly message if there is not enough data.

### Validation Service

- Central `ValidationService` handles:
  - Budget validation  
  - Transaction amount and description validation  
- Prevents saving invalid data and shows inline error messages.

### Data Persistence

- Budget and transactions are saved to **LocalStorage** whenever they change.  
- On app start:
  - Existing data is loaded into `BudgetContext` and `TransactionContext`.  
  - If nothing exists, default values are used.

---

## 3. Architecture & Design

### High-Level Architecture

- **React Components**
  - `BudgetInput`
  - `DashboardSummary`
  - `TransactionsList`
  - `SpendingChart`
- **Context Layer**
  - `BudgetContext` – holds current budget and remaining amount.
  - `TransactionContext` – holds income/expense transactions.
- **Services**
  - `ValidationService` – reusable input validation logic.
  - `storageService` (or similar) – wrapper for LocalStorage access.

### Data Flow (User Flow Summary)

1. User opens the app → Dashboard loads budget + transactions from LocalStorage.  
2. User enters a budget or transaction.  
3. `ValidationService` validates the input.  
4. If invalid → error message shown; nothing is saved.  
5. If valid → `BudgetContext` / `TransactionContext` update state.  
6. Updated data is saved to LocalStorage.  
7. Dashboard + Chart rerender, showing the latest financial summary.


---

## 4. Functional & Non-Functional Requirements

The full list of **Functional Requirements (FR1–FR7)** and **Non-Functional Requirements (NFR1–NFR5)** is documented in the project report.

Examples:

- **FR1–FR2**: Define and update a monthly budget.  
- **FR3**: Automatic remaining budget calculation with thresholds.  
- **FR4–FR5**: Dashboard summary + spending vs budget chart.  
- **FR6**: Centralized validation for all inputs.  
- **FR7**: Persistent storage using LocalStorage.

Non-functional areas include **Usability, Performance, Scalability, Maintainability, and Compatibility.**

---

## 5. Project Management (GitHub Projects)

The team used **GitHub Projects** to manage work:

- One EPIC:

  - `EPIC: Monthly Budget Feature (Define, Update & Manage Monthly Budget)`  

- Issue groups:
  - **Requirements & Documentation**
  - **Feature Development (Context, Dashboard, Chart)**
  - **Validation & Bug Fixing**
  - **Testing & QA**
- Columns:
  - `Backlog` → `Ready` → `In Progress` → `In Review` → `Done`
- Each issue has:
  - Clear title and description
  - Labels (backend, frontend, enhancement, validation, QA, etc.)
  - Linked to the EPIC where appropriate
  - Assigned to one or more team members

This structure demonstrates traceability from requirements → tasks → implementation.

---

## 6. Technology Stack

- **Frontend:** React.js, JavaScript (ES6+)  
- **State Management:** React Context API  
- **Charting:** Recharts (or another React chart library)  
- **Styling:** CSS / Flexbox / basic responsive design  
- **Persistence:** Browser LocalStorage  
- **Tools:** Git, GitHub Projects, VS Code

---

## 7. Getting Started (Run Locally)

### Prerequisites

- Node.js (LTS) and npm installed  
- Git installed

### Clone the Repository

 bash
git clone https://github.com/Rahul26240/expense-tracker-react.git
cd expense-tracker-react


### Git Commit Practices

The project follows a clean and professional Git commit strategy to ensure clarity and traceability throughout development.

### Commit Message Format
All commits follow the structure:

<type>(scope): short description  #issue-number

Example:
feat(budget): implement BudgetContext and monthly budget state #15

### Commit Types Used
- feat: new features
- fix: bug fixes
- refactor: code restructuring
- style: UI or formatting updates
- docs: documentation changes
- test: test case additions
- chore: cleanup, maintenance tasks

### Example Commit Messages
- feat(ui): create BudgetInput component with inline validation #16  
- feat(logic): add remaining budget calculation and state updates #19  
- feat(dashboard): implement DashboardSummary with status indicator #20  
- feat(chart): integrate Recharts for Spending vs Budget visualization #21  
- fix(validation): enforce numeric rules for budget field #24  
- chore(storage): enable LocalStorage persistence for budget and transactions #27  
- test(plan): add initial functional test cases #29  
- docs(readme): update project documentation and diagrams #32  

### Why This Matters
- Ensures each commit represents one clear, isolated change  
- Improves project maintainability  
- Makes debugging easier  
- Demonstrates professional engineering practices  
- Maintains full traceability between requirements, issues, and implementation  

This commit strategy aligns with industry standards and supports full project transparency.
