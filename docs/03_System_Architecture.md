# AlgoMentor – System Architecture

| Property       | Value               |
| -------------- | ------------------- |
| **Project**    | AlgoMentor          |
| **Document**   | System Architecture |
| **Version**    | 1.0.0               |
| **Author**     | Sujith TR           |
| **Created On** | 04 July 2026        |
| **Status**     | Draft               |

---

# Revision History

| Version | Date         | Description                 |
| ------- | ------------ | --------------------------- |
| 1.0.0   | 04 July 2026 | Initial System Architecture |

---

# 1. Introduction

This document describes the overall architecture of the AlgoMentor platform.

Its purpose is to explain how different modules communicate with each other and how data flows through the system.

This document does **not** describe implementation details or source code. It focuses only on the overall system design.

---

# 2. Architecture Overview

AlgoMentor follows a Client–Server Architecture.

The frontend is responsible for the user interface.

The backend is responsible for business logic, authentication, database operations, code execution, and AI communication.

The AI Logic Engine is treated as an independent service that analyzes the student's code and returns learning-oriented feedback.

---

# 3. High-Level Architecture

```
                    Student

                       │

                       ▼

             React Frontend (Vite)

                       │

                 REST API (Axios)

                       │

                       ▼

            Django REST Framework Backend

 ┌──────────────┬──────────────┬──────────────┐
 │              │              │              │
 │ Authentication│ Questions    │ Submissions │
 │              │              │              │
 └──────────────┴──────────────┴──────────────┘

            │                    │

            ▼                    ▼

     Code Execution       AI Logic Engine

            │                    │

            └────────────┬─────────────┘

                         ▼

                  PostgreSQL Database
```

---

# 4. System Components

## 4.1 React Frontend

Responsibilities

* User Interface
* Login & Registration
* Dashboard
* Question List
* Code Editor
* Output Display
* Algorithm Display
* Score Display

The frontend never communicates directly with the database or the AI service.

All communication happens through the Django backend.

---

## 4.2 Django REST Backend

Responsibilities

* Authentication
* Authorization
* Business Logic
* API Endpoints
* Database Management
* Code Execution Requests
* AI Requests
* Score Calculation

The backend acts as the central controller of the entire application.

---

## 4.3 Database

Initially PostgreSQL will be used.

During local development SQLite may be used.

Responsibilities

* User Information
* Questions
* Submissions
* Scores
* Future Analytics

---

## 4.4 Code Execution Module

Purpose

Safely execute the student's Python program.

Responsibilities

* Execute code
* Capture output
* Capture runtime errors
* Return execution results

This module does not evaluate logic.

It only executes the code.

---

## 4.5 AI Logic Engine

Purpose

Help students understand their own programming logic.

Current Responsibilities

* Analyze the student's code
* Generate algorithm
* Explain the student's logic
* Identify missing logical steps
* Suggest improvements without revealing the complete solution

Future Responsibilities

* Logic Score
* Flowchart Generation
* Dry Run Visualization
* Complexity Analysis
* Hint Generation
* Code Review

---

# 5. User Workflow

## Student Workflow

```
Login

↓

Dashboard

↓

Choose Question

↓

Write Code

↓

Click "Evaluate My Logic"

↓

Backend sends Question + Code

↓

AI Logic Engine analyzes

↓

Algorithm Returned

↓

Student improves code

↓

Click "Run Code"

↓

Code Execution Module

↓

Output Displayed

↓

Click "Submit Solution"

↓

Backend compares output

↓

Score Generated

↓

Submission Stored

↓

Dashboard Updated
```

---

## Administrator Workflow

```
Admin Login

↓

Dashboard

↓

Manage Questions

↓

Manage Students

↓

View Submissions

↓

View Scores
```

---

# 6. Module Responsibilities

| Module            | Responsibility                          |
| ----------------- | --------------------------------------- |
| Authentication    | Login, Registration, JWT                |
| Question Module   | Question Management                     |
| Code Editor       | Student Code Writing                    |
| Code Execution    | Run Python Code                         |
| AI Logic Engine   | Logic Evaluation & Algorithm Generation |
| Submission Module | Store Solutions                         |
| Dashboard         | Progress & Analytics                    |

---

# 7. Communication Flow

### Evaluate My Logic

Student

↓

Frontend

↓

Backend

↓

AI Logic Engine

↓

Backend

↓

Frontend

↓

Algorithm Display

---

### Run Code

Student

↓

Frontend

↓

Backend

↓

Code Execution Module

↓

Backend

↓

Frontend

↓

Output Panel

---

### Submit Solution

Student

↓

Frontend

↓

Backend

↓

Run Code

↓

Compare Expected Output

↓

Generate Score

↓

Store Submission

↓

Update Dashboard

---

# 8. Design Principles

AlgoMentor follows the following architectural principles:

* Separation of Concerns
* Modular Design
* RESTful Architecture
* Scalability
* Maintainability
* Security by Design
* Reusable Components
* AI as an Independent Service

---

# 9. Scalability

The architecture has been designed so that future versions can support:

* Multiple Programming Languages
* Multiple AI Providers
* Teacher Dashboard
* Student Analytics
* Coding Contests
* AI Interview Mode
* Live Coding Sessions
* Classroom Management
* Mobile Application

No major architectural changes should be required to support these features.

---

# 10. Conclusion

The architecture of AlgoMentor separates the frontend, backend, code execution, and AI logic engine into independent modules.

This modular design ensures that the platform remains scalable, maintainable, and ready for future expansion while providing students with an intelligent learning experience focused on programming logic rather than memorizing syntax.
