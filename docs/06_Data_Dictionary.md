# AlgoMentor – Data Dictionary

| Property       | Value           |
| -------------- | --------------- |
| **Project**    | AlgoMentor      |
| **Document**   | Data Dictionary |
| **Version**    | 1.0.0           |
| **Author**     | Sujith TR       |
| **Created On** | 04 July 2026    |
| **Status**     | Draft           |

---

# Revision History

| Version | Date         | Description             |
| ------- | ------------ | ----------------------- |
| 1.0.0   | 04 July 2026 | Initial Data Dictionary |

---

# 1. Introduction

The Data Dictionary defines every entity, field, data type, validation rule, and purpose used in the AlgoMentor database.

This document acts as the primary reference while creating Django models and database migrations.

---

# 2. User Entity

## Description

Represents every authenticated account in the system.

---

| Field      | Data Type      | Required | Description                             |
| ---------- | -------------- | -------- | --------------------------------------- |
| id         | UUID / Integer | Yes      | Unique identifier for the user          |
| full_name  | String         | Yes      | User's full name                        |
| email      | Email          | Yes      | Login email (Must be unique)            |
| password   | Hashed String  | Yes      | Encrypted password                      |
| role       | Choice         | Yes      | Student, Instructor or Admin            |
| is_active  | Boolean        | Yes      | Indicates whether the account is active |
| created_at | DateTime       | Yes      | Account creation time                   |
| updated_at | DateTime       | Yes      | Last modification time                  |

---

## Reserved for Future Versions

* profile_picture
* bio
* experience_points
* streak
* preferred_language
* github_profile
* linkedin_profile

---

# 3. Question Entity

## Description

Stores programming questions available for students.

---

| Field              | Data Type      | Required | Description                       |
| ------------------ | -------------- | -------- | --------------------------------- |
| id                 | UUID / Integer | Yes      | Unique identifier                 |
| title              | String         | Yes      | Question title                    |
| slug               | String         | Yes      | URL-friendly title                |
| difficulty         | Choice         | Yes      | Easy, Medium, Hard                |
| description        | Text           | Yes      | Complete problem statement        |
| input_format       | Text           | Yes      | Input specification               |
| output_format      | Text           | Yes      | Output specification              |
| constraints        | Text           | No       | Problem constraints               |
| sample_input       | Text           | Yes      | Example input                     |
| sample_output      | Text           | Yes      | Example output                    |
| sample_explanation | Text           | No       | Explanation of sample             |
| hints              | Text           | No       | Hint for solving                  |
| starter_code       | Text           | No       | Initial code template             |
| estimated_time     | Integer        | No       | Expected solving time in minutes  |
| is_active          | Boolean        | Yes      | Whether the question is available |
| created_at         | DateTime       | Yes      | Creation timestamp                |
| updated_at         | DateTime       | Yes      | Last update timestamp             |

---

# 4. Test Case Entity

## Description

Stores all test cases related to a programming question.

---

| Field           | Data Type      | Required | Description                      |
| --------------- | -------------- | -------- | -------------------------------- |
| id              | UUID / Integer | Yes      | Unique identifier                |
| question        | Foreign Key    | Yes      | Related Question                 |
| input           | Text           | Yes      | Test input                       |
| expected_output | Text           | Yes      | Expected output                  |
| is_sample       | Boolean        | Yes      | Whether visible to students      |
| weight          | Integer        | No       | Marks assigned to this test case |

---

# 5. Submission Entity

## Description

Represents every solution submitted by a student.

---

| Field            | Data Type      | Required | Description                                             |
| ---------------- | -------------- | -------- | ------------------------------------------------------- |
| id               | UUID / Integer | Yes      | Unique identifier                                       |
| student          | Foreign Key    | Yes      | Related User                                            |
| question         | Foreign Key    | Yes      | Related Question                                        |
| language         | Choice         | Yes      | Programming language                                    |
| source_code      | Text           | Yes      | Submitted code                                          |
| execution_output | Text           | No       | Program output                                          |
| execution_error  | Text           | No       | Runtime error details                                   |
| score            | Integer        | Yes      | Marks obtained                                          |
| status           | Choice         | Yes      | Correct, Wrong Answer, Runtime Error, Compilation Error |
| execution_time   | Float          | No       | Program execution time                                  |
| memory_used      | Float          | No       | Memory consumption                                      |
| submitted_at     | DateTime       | Yes      | Submission timestamp                                    |

---

# 6. Choice Values

## User Roles

* Student
* Instructor
* Administrator

---

## Difficulty Levels

* Easy
* Medium
* Hard

---

## Submission Status

* Pending
* Correct
* Wrong Answer
* Runtime Error
* Compilation Error
* Time Limit Exceeded

---

# 7. Naming Conventions

The following naming conventions will be used throughout the database.

## Tables

* Singular names
* PascalCase in documentation
* Snake_case for database tables if required

Examples

* User
* Question
* Submission
* TestCase

---

## Fields

Rules

* Lowercase
* Snake Case
* Descriptive names
* No abbreviations

Examples

* full_name
* sample_output
* execution_time
* created_at

---

# 8. Validation Rules

General validation rules:

* Email must be unique.
* Passwords must be encrypted.
* Question titles cannot be empty.
* Difficulty must be one of the predefined choices.
* Scores cannot be negative.
* Source code cannot be empty during submission.

---

# 9. Future Fields

The following fields are reserved for future versions.

## User

* badges
* achievements
* coding_streak
* total_xp

---

## Question

* tags
* company
* category
* video_solution

---

## Submission

* ai_feedback
* logic_score
* time_complexity
* space_complexity
* flowchart
* dry_run_steps

---

# 10. Conclusion

The Data Dictionary defines every field used by the AlgoMentor system.

It serves as the reference document for:

* Django Model Creation
* Serializer Design
* API Development
* Database Validation
* Future Expansion

Any modification to the database structure should first be reflected in this document before implementation.
