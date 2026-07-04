# AlgoMentor – AI Logic Engine Design

| Property       | Value                  |
| -------------- | ---------------------- |
| **Project**    | AlgoMentor             |
| **Document**   | AI Logic Engine Design |
| **Version**    | 1.0.0                  |
| **Author**     | Sujith TR              |
| **Created On** | 04 July 2026           |
| **Status**     | Draft                  |

---

# Revision History

| Version | Date         | Description                    |
| ------- | ------------ | ------------------------------ |
| 1.0.0   | 04 July 2026 | Initial AI Logic Engine Design |

---

# 1. Introduction

The AI Logic Engine is the core intelligent component of AlgoMentor.

Unlike traditional online coding platforms that simply verify whether a solution is correct, the AI Logic Engine focuses on understanding the student's programming logic and helping them improve their problem-solving skills.

The AI is intended to act as a mentor rather than an answer provider.

---

# 2. Purpose

The AI Logic Engine is responsible for:

* Understanding the student's current solution.
* Generating an easy-to-understand algorithm.
* Explaining the student's logic.
* Identifying missing logical steps.
* Providing constructive feedback.
* Encouraging independent problem solving.

---

# 3. Design Philosophy

The AI should follow these principles.

* Teach logic before syntax.
* Encourage learning instead of copying.
* Avoid giving the complete answer.
* Explain rather than solve.
* Provide beginner-friendly explanations.
* Adapt to incomplete code.

---

# 4. User Workflow

Student

↓

Open Question

↓

Write Code

↓

Click **Evaluate My Logic**

↓

Frontend sends:

* Question
* Student Code
* Programming Language

↓

Backend

↓

AI Logic Engine

↓

AI Analysis

↓

Return Response

↓

Display Algorithm & Feedback

---

# 5. AI Input

The AI receives the following information.

## Question Details

* Title
* Problem Statement
* Difficulty

---

## Student Code

The complete source code currently written by the student.

---

## Programming Language

Initially:

* Python

Future:

* Java
* C
* C++
* JavaScript

---

# 6. AI Output

The AI should return structured information.

---

## Algorithm

Example

1. Create a list.
2. Assume the first value as the largest.
3. Traverse every element.
4. Compare each element.
5. Update the largest value.
6. Display the result.

---

## Logic Status

Possible values:

* Complete
* Partially Complete
* Incomplete
* Incorrect

---

## Feedback

Examples:

* Your loop structure is correct.
* The comparison logic is missing.
* Variable initialization is good.
* Consider handling edge cases.

---

## Suggestions

Suggestions should improve understanding without revealing the final answer.

Example:

Instead of:

"Use max()"

Prefer:

"Think about comparing each element with the current largest value."

---

# 7. AI Response Format

The backend expects the AI to return a structured JSON response.

Example

```json
{
    "logic_status":"Partially Complete",

    "algorithm":[
        "Create a list",
        "Initialize the first element",
        "Traverse the list"
    ],

    "feedback":[
        "Good initialization.",
        "Comparison logic is missing."
    ],

    "suggestions":[
        "Think about comparing every element."
    ]
}
```

---

# 8. AI Safety Rules

The AI must NOT:

* Generate the full solution automatically.
* Reveal hidden test cases.
* Encourage plagiarism.
* Ignore invalid code.
* Produce harmful or unsafe content.

The AI should always encourage learning.

---

# 9. Prompt Engineering Strategy

The backend will generate prompts that include:

* Question details
* Student code
* Programming language
* Desired response format

The prompt should instruct the AI to:

* Explain logic.
* Generate an algorithm.
* Avoid giving the final solution.
* Keep explanations beginner-friendly.

---

# 10. Future AI Features

Future versions may include:

* Logic Score
* Time Complexity Analysis
* Space Complexity Analysis
* Dry Run Visualization
* Flowchart Generation
* AI Code Review
* Hint Generation
* Code Quality Analysis
* Personalized Learning Suggestions

---

# 11. Error Handling

If the AI cannot analyze the code:

* Return an appropriate message.
* Do not crash the application.
* Allow the student to continue coding.

Example

"Unable to evaluate the current code. Please ensure your code is syntactically valid."

---

# 12. Performance Considerations

The AI should only be called when the student clicks:

**Evaluate My Logic**

The AI will NOT be called during:

* Typing
* Running Code
* Submission

This reduces unnecessary API requests and keeps the application responsive.

---

# 13. Scalability

The AI Logic Engine should support future integration with multiple AI providers.

Examples:

* OpenAI
* Azure OpenAI
* Anthropic
* Google Gemini
* Self-hosted models

The backend should communicate through a common AI service layer so that providers can be changed without affecting the frontend.

---

# 14. Success Criteria

The AI Logic Engine is considered successful if it:

* Improves students' logical thinking.
* Generates accurate algorithms.
* Provides meaningful feedback.
* Encourages independent problem solving.
* Remains responsive and scalable.

---

# 15. Conclusion

The AI Logic Engine is the defining feature of AlgoMentor.

Its purpose is not to solve programming problems for students but to help them understand their own logic and improve their algorithmic thinking through guided feedback.
