# AlgoMentor – Entity Relationship Diagram (ERD)

| Property       | Value                       |
| -------------- | --------------------------- |
| **Project**    | AlgoMentor                  |
| **Document**   | Entity Relationship Diagram |
| **Version**    | 1.0.0                       |
| **Author**     | Sujith TR                   |
| **Created On** | 04 July 2026                |
| **Status**     | Draft                       |

---

# Revision History

| Version | Date         | Description                 |
| ------- | ------------ | --------------------------- |
| 1.0.0   | 04 July 2026 | Initial ER Diagram document |

---

# 1. Introduction

This document describes the relationships between the core entities of the AlgoMentor system.

The purpose of the Entity Relationship Diagram (ERD) is to provide a visual and logical understanding of how data is connected inside the application.

This document serves as the reference for database implementation during backend development.

---

# 2. Core Entities

The Version 1.0 database contains the following entities:

* User
* Question
* Test Case
* Submission

These entities are sufficient to support the first release of AlgoMentor.

---

# 3. Entity Relationship Diagram

```text
                     +----------------+
                     |      User      |
                     +----------------+
                     | PK id          |
                     | name           |
                     | email          |
                     | password       |
                     | role           |
                     +----------------+
                              |
                              | 1
                              |
                              |
                              | N
                     +----------------+
                     |   Submission   |
                     +----------------+
                     | PK id          |
                     | FK user_id     |
                     | FK question_id |
                     | code           |
                     | output         |
                     | score          |
                     | status         |
                     +----------------+
                              ^
                              |
                              | N
                              |
                              | 1
                     +----------------+
                     |    Question    |
                     +----------------+
                     | PK id          |
                     | title          |
                     | difficulty     |
                     | description    |
                     +----------------+
                              |
                              | 1
                              |
                              |
                              | N
                     +----------------+
                     |   Test Case    |
                     +----------------+
                     | PK id          |
                     | FK question_id |
                     | input          |
                     | expected_output|
                     | is_sample      |
                     +----------------+
```

---

# 4. Relationship Explanation

## User → Submission

Relationship Type:

One-to-Many (1:N)

Explanation:

A single student can submit solutions for multiple programming questions.

Each submission belongs to exactly one student.

Example:

Student

↓

Question 1

↓

Question 2

↓

Question 3

↓

Three different submissions.

---

## Question → Submission

Relationship Type:

One-to-Many (1:N)

Explanation:

A programming question can be solved by many students.

Each submission belongs to only one question.

Example:

Question

↓

Student A Submission

↓

Student B Submission

↓

Student C Submission

---

## Question → Test Case

Relationship Type:

One-to-Many (1:N)

Explanation:

Each programming question contains multiple test cases.

Example:

Question

↓

Sample Test Case

↓

Hidden Test Case 1

↓

Hidden Test Case 2

↓

Hidden Test Case 3

---

# 5. Cardinality Summary

| Parent Entity | Child Entity | Relationship |
| ------------- | ------------ | ------------ |
| User          | Submission   | One-to-Many  |
| Question      | Submission   | One-to-Many  |
| Question      | Test Case    | One-to-Many  |

---

# 6. Primary Keys

Each entity contains a Primary Key (PK).

| Entity     | Primary Key |
| ---------- | ----------- |
| User       | id          |
| Question   | id          |
| Submission | id          |
| Test Case  | id          |

Future versions may replace integer IDs with UUIDs.

---

# 7. Foreign Keys

Foreign Keys establish relationships between entities.

| Entity     | Foreign Key | References |
| ---------- | ----------- | ---------- |
| Submission | user_id     | User       |
| Submission | question_id | Question   |
| Test Case  | question_id | Question   |

---

# 8. Data Flow

Student registers

↓

User record created

↓

Admin creates Question

↓

Question stored

↓

Admin creates Test Cases

↓

Test cases linked to Question

↓

Student solves Question

↓

Submission created

↓

Score stored

↓

Dashboard retrieves submission history

---

# 9. Future Relationships

The current ERD has been intentionally designed to support future expansion.

Future entities may include:

* Badge
* Achievement
* Contest
* Classroom
* Course
* Certificate
* Notification
* Leaderboard

These entities can be added without changing the existing relationships.

---

# 10. Design Principles

The ERD follows the following principles:

* Minimal redundancy
* Normalized relationships
* Simple foreign key structure
* Easy scalability
* Maintainability
* Extensibility

---

# 11. Conclusion

The Entity Relationship Diagram defines the logical relationships between all core entities of AlgoMentor.

The database has been designed with simplicity, scalability, and future expansion in mind.

This ERD will serve as the reference when implementing Django models during the backend development phase.
