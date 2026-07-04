# AlgoMentor – Database Design

| Property       | Value           |
| -------------- | --------------- |
| **Project**    | AlgoMentor      |
| **Document**   | Database Design |
| **Version**    | 1.0.0           |
| **Author**     | Sujith TR       |
| **Created On** | 04 July 2026    |
| **Status**     | Draft           |

---

# Revision History

| Version | Date         | Description                      |
| ------- | ------------ | -------------------------------- |
| 1.0.0   | 04 July 2026 | Initial database design document |

---

# 1. Introduction

This document describes the conceptual database design of the AlgoMentor platform.

The primary objective of the database is to store user information, programming questions, test cases, and student submissions while maintaining a scalable, secure, and maintainable structure.

This document focuses on the logical design of the database and does not contain implementation-specific details such as Django models or SQL scripts.

---

# 2. Objectives

The database has been designed with the following goals:

* Store data efficiently.
* Eliminate unnecessary duplication.
* Support future expansion.
* Maintain data integrity.
* Provide fast retrieval of frequently accessed information.
* Keep relationships simple and easy to maintain.

---

# 3. Database Technology

## Development Environment

* SQLite

SQLite will be used during the initial development phase because it is lightweight, requires no additional installation, and integrates seamlessly with Django.

## Production Environment

* PostgreSQL

PostgreSQL will be used in production because it offers:

* Better scalability
* High performance
* Advanced indexing
* Strong security
* Excellent support for large applications

---

# 4. Database Design Principles

The AlgoMentor database follows the following principles:

* Separation of Concerns
* Data Integrity
* Normalization
* Scalability
* Maintainability
* Minimal Data Redundancy
* Secure Data Storage
* Future Expandability

---

# 5. Core Entities

Version 1.0 of AlgoMentor contains the following core entities:

1. User
2. Question
3. Test Case
4. Submission

These four entities are sufficient to support the initial version of the application while leaving room for future expansion.

---

# 6. Entity Overview

## User

Represents every authenticated account in the system.

Responsibilities:

* Authentication
* Authorization
* Student Profile
* Administrator Profile
* Instructor Profile (Future)

The User entity does not store calculated information such as the total score.

---

## Question

Represents a programming problem available to students.

Each question contains all information required to understand and solve the problem.

Examples include:

* Title
* Description
* Difficulty
* Constraints
* Input Format
* Output Format
* Sample Input
* Sample Output
* Hints
* Starter Code

A single question may contain multiple test cases.

---

## Test Case

Each programming question can have one or more test cases.

Every test case contains:

* Input
* Expected Output

Some test cases may be marked as sample test cases that are visible to students.

Additional hidden test cases may be used during submission evaluation.

---

## Submission

Represents a student's attempt to solve a programming question.

Each submission stores:

* Student
* Question
* Source Code
* Programming Language
* Program Output
* Runtime Errors
* Score
* Execution Status
* Submission Time

Every submission belongs to exactly one student and one programming question.

---

# 7. Entity Relationships

The relationships between entities are defined as follows.

## User → Submission

One User can create many Submissions.

Each Submission belongs to one User.

Relationship:

One-to-Many

---

## Question → Submission

One Question can have many Submissions.

Each Submission belongs to one Question.

Relationship:

One-to-Many

---

## Question → Test Case

One Question can contain multiple Test Cases.

Each Test Case belongs to one Question.

Relationship:

One-to-Many

---

# 8. Conceptual Database Structure

The conceptual database structure is illustrated below.

```text
                 User
                   │
                   │ 1
                   │
                   │
                   ▼
             Submission
                   ▲
                   │
                   │
                   │ N
                   │
                   │
                 Question
                   │
                   │ 1
                   │
                   ▼
               Test Case
```

---

# 9. Data Storage Strategy

The database stores only permanent information.

Examples of permanent data include:

* User Accounts
* Programming Questions
* Test Cases
* Student Submissions

Temporary information is **not stored**.

Examples include:

* AI-generated algorithms
* Logic evaluation results
* Code execution output before submission
* Temporary editor content

These are generated when required and discarded after use.

This approach keeps the database lightweight and reduces unnecessary storage.

---

# 10. Soft Delete Strategy

Records should not be permanently deleted unless absolutely necessary.

Instead, inactive records should be marked using an "Active" status.

Examples:

* Deactivate Questions
* Deactivate Users

This preserves submission history and prevents accidental data loss.

---

# 11. Timestamp Strategy

Every major entity should include timestamps.

Examples:

* Created Date
* Updated Date

These fields help with:

* Auditing
* Reporting
* Analytics
* Debugging
* Future dashboards

---

# 12. Security Considerations

The database should follow these security practices:

* Passwords must never be stored in plain text.
* Passwords will be securely hashed using Django's authentication system.
* Sensitive operations must require authentication.
* Database access must be restricted to the backend server.
* Students must never access the database directly.

---

# 13. Future Expansion

The database has been designed to support additional entities in future versions without major restructuring.

Possible future entities include:

* Badge
* Achievement
* Contest
* Classroom
* Course
* Notification
* Certificate
* Leaderboard
* AI Evaluation History
* Discussion Forum

These entities are intentionally excluded from Version 1.0 to keep the initial implementation simple.

---

# 14. Conclusion

The AlgoMentor database is designed using a modular and scalable approach.

The initial version focuses on four core entities:

* User
* Question
* Test Case
* Submission

This design provides a strong foundation for the current application while allowing future features to be added with minimal architectural changes.
