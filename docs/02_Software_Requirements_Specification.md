# AlgoMentor – Software Requirements Specification (SRS)

## Version

**0.1.0**

---

# 1. Introduction

## 1.1 Purpose

The purpose of AlgoMentor is to provide an AI-assisted programming practice platform that helps students improve their programming logic through coding exercises, algorithm generation, and intelligent feedback.

---

## 1.2 Scope

AlgoMentor allows students to:

* Register and log in.
* Solve programming questions.
* Write Python code.
* Execute code safely.
* View the output.
* Receive a live AI-generated algorithm based on their code.
* Submit their solution.
* Receive an automatic score.

Administrators can:

* Manage users.
* Manage programming questions.
* Monitor submissions.

---

# 2. User Roles

## Student

Students can:

* Register
* Login
* View dashboard
* View questions
* Write code
* Execute code
* View output
* View generated algorithm
* Submit solutions
* View scores
* View submission history

---

## Administrator

Administrators can:

* Login
* Manage students
* Manage questions
* View submissions
* View scores
* Activate or deactivate users

---

# 3. Functional Requirements

## Authentication

* User Registration
* User Login
* JWT Authentication
* Logout
* Protected Routes

---

## Question Management

* View all questions
* View question details
* Display sample input
* Display expected output

Administrator:

* Add question
* Edit question
* Delete question

---

## Code Editor

The system shall provide:

* Python syntax highlighting
* Line numbers
* Auto indentation
* Code editing

---

## Code Execution

The system shall:

* Execute Python code securely
* Display program output
* Display runtime errors
* Display execution status

---

## AI Algorithm Generator

The system shall:

* Monitor the user's code while typing
* Generate an algorithm after a short pause
* Update the algorithm as the code changes

---

## Submission

The system shall:

* Store submitted code
* Compare output with expected output
* Generate a score
* Store submission history

---

## Dashboard

Students shall be able to view:

* Total solved questions
* Total score
* Recent submissions

Administrators shall be able to view:

* Total users
* Total questions
* Recent submissions

---

# 4. Non-Functional Requirements

## Performance

* Fast page loading
* Quick code execution
* Efficient API responses

---

## Security

* JWT Authentication
* Password hashing
* Protected APIs
* Secure code execution

---

## Scalability

The system should support:

* Thousands of users
* Thousands of questions
* Multiple programming languages in future

---

## Maintainability

The project should follow:

* Modular architecture
* Clean code
* Reusable components
* RESTful API principles

---

# 5. Constraints

Version 1 supports:

* Python only
* Single administrator
* Basic scoring based on output comparison

---

# 6. Assumptions

It is assumed that:

* Users have basic Python knowledge.
* Internet connectivity is available.
* AI services are available for algorithm generation.

---

# 7. Future Scope

Future versions may include:

* Multiple programming languages
* AI hints
* Flowcharts
* Dry-run visualization
* Logic score
* AI code review
* Teacher dashboard
* Student analytics
* Coding contests
* Certificates
* Mobile application

---

# 8. Success Criteria

The project will be considered successful if students can:

* Improve problem-solving skills.
* Understand algorithms better.
* Practice programming regularly.
* Receive meaningful feedback from AI.
