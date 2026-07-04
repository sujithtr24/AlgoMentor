# AlgoMentor – API Documentation

| Property       | Value             |
| -------------- | ----------------- |
| **Project**    | AlgoMentor        |
| **Document**   | API Documentation |
| **Version**    | 1.0.0             |
| **Author**     | Sujith TR         |
| **Created On** | 04 July 2026      |
| **Status**     | Draft             |

---

# Revision History

| Version | Date         | Description        |
| ------- | ------------ | ------------------ |
| 1.0.0   | 04 July 2026 | Initial API Design |

---

# 1. Introduction

This document defines all REST APIs used by the AlgoMentor platform.

The APIs follow REST principles and communicate using JSON.

All endpoints are prefixed with:

```
/api/
```

---

# 2. Authentication APIs

---

## Register

```
POST /api/auth/register/
```

Purpose

Create a new student account.

Authentication Required

No

Request

```json
{
    "full_name": "John Doe",
    "email": "john@gmail.com",
    "password": "********"
}
```

Response

```json
{
    "message":"Registration Successful"
}
```

---

## Login

```
POST /api/auth/login/
```

Authentication Required

No

Request

```json
{
    "email":"john@gmail.com",
    "password":"********"
}
```

Response

```json
{
    "access":"JWT_TOKEN",
    "refresh":"JWT_REFRESH_TOKEN"
}
```

---

## Profile

```
GET /api/auth/profile/
```

Authentication Required

Yes

Response

```json
{
    "id":1,
    "full_name":"John Doe",
    "email":"john@gmail.com"
}
```

---

# 3. Question APIs

---

## Get All Questions

```
GET /api/questions/
```

Authentication Required

Yes

Returns

* Question List

---

## Get Question Details

```
GET /api/questions/{id}/
```

Returns

* Question
* Sample Input
* Sample Output
* Difficulty
* Description

---

# 4. AI Logic Engine APIs

---

## Evaluate My Logic

```
POST /api/logic/evaluate/
```

Authentication Required

Yes

Purpose

Analyzes the student's code and generates algorithmic feedback.

Request

```json
{
    "question_id":1,
    "language":"python",
    "source_code":"print('Hello')"
}
```

Response

```json
{
    "algorithm":[
        "Create output",
        "Print Hello"
    ],
    "logic_status":"Complete",
    "suggestions":[
        "Good use of print statement."
    ]
}
```

---

# 5. Code Execution APIs

---

## Run Code

```
POST /api/compiler/run/
```

Authentication Required

Yes

Purpose

Execute the student's code without storing the submission.

Request

```json
{
    "language":"python",
    "source_code":"print('Hello')"
}
```

Response

```json
{
    "output":"Hello",
    "error":"",
    "execution_time":"0.02"
}
```

---

# 6. Submission APIs

---

## Submit Solution

```
POST /api/submissions/
```

Authentication Required

Yes

Purpose

Submit the student's final solution for evaluation.

Request

```json
{
    "question_id":1,
    "language":"python",
    "source_code":"print('Hello')"
}
```

Response

```json
{
    "score":100,
    "status":"Correct",
    "submission_id":25
}
```

---

## Submission History

```
GET /api/submissions/
```

Returns

Student's previous submissions.

---

# 7. Dashboard APIs

---

## Dashboard

```
GET /api/dashboard/
```

Returns

```json
{
    "questions_solved":10,
    "total_score":890,
    "accuracy":92,
    "recent_submissions":[]
}
```

---

# 8. Admin APIs

Administrator only.

---

## Manage Questions

```
POST /api/admin/questions/
PUT /api/admin/questions/{id}/
DELETE /api/admin/questions/{id}/
```

---

## Manage Users

```
GET /api/admin/users/
```

```
PUT /api/admin/users/{id}/
```

---

## Dashboard

```
GET /api/admin/dashboard/
```

Returns

* Total Students
* Total Questions
* Total Submissions

---

# 9. Common HTTP Status Codes

| Code | Meaning               |
| ---- | --------------------- |
| 200  | Success               |
| 201  | Created               |
| 400  | Bad Request           |
| 401  | Unauthorized          |
| 403  | Forbidden             |
| 404  | Not Found             |
| 500  | Internal Server Error |

---

# 10. Authentication

Protected APIs require JWT Authentication.

Authorization Header

```
Authorization: Bearer <access_token>
```

---

# 11. Future APIs

The following APIs are reserved for future versions.

* Hint Generation API
* Flowchart API
* Dry Run API
* Complexity Analysis API
* Contest API
* Classroom API
* Leaderboard API
* Certificate API

---

# 12. API Design Principles

The AlgoMentor API follows these principles.

* RESTful Architecture
* Stateless Communication
* JSON Request/Response
* Secure Authentication
* Modular Endpoints
* Scalable Design

---

# 13. Conclusion

The API architecture separates authentication, question management, code execution, AI logic evaluation, submissions, dashboards, and administration into independent modules.

This modular approach allows future expansion without affecting the existing API structure.
