# Annex Technologies Limited — Technical Assessment

**Congratulations on reaching the technical assessment stage!**

This assessment is designed to evaluate your problem-solving skills, coding proficiency, and ability to work across multiple programming domains. Please read the instructions carefully before beginning.

---

## 📋 Assessment Overview

- **Duration:** 2 hours
- **Total Questions:** 3 (covering C, MySQL, and C++)
- **Required Submissions:** 3 source files
- **Evaluation Focus:** Correctness, efficiency, code quality, and edge case handling

---

## 📝 General Instructions

1. You have **2 hours** to complete this assessment.
2. Read each question thoroughly before attempting to solve it.
3. You may use online resources and documentation, but **AI code generators (ChatGPT, GitHub Copilot, etc.) are strictly prohibited**.
4. Submit your solutions as separate files with the following names:
   - `pth_factor.c`
   - `top_students.sql`
   - `top_articles.cpp`
5. Ensure all code compiles and runs without errors.
6. Test your solutions with the provided sample inputs before submission.

---

## 🧪 Question 1: Find the p-th Factor (C)

### Problem Statement

Given two integers, `n` and `p`, find the **p-th smallest factor** of `n`.

A factor of `n` is any positive integer that divides `n` with no remainder.

### Requirements

- Find all positive factors of `n`
- Sort them in ascending order
- Return the **p-th smallest factor** (using 1-based indexing)
- If `n` has fewer than `p` factors, return `0`

### Constraints

- `1 ≤ n ≤ 10¹⁵`
- `1 ≤ p ≤ 10⁹`

### Example

**Input:** `n = 10, p = 3`  
**Output:** `5`

**Explanation:**  
Factors of 10: `{1, 2, 5, 10}`  
The 3rd factor is `5`.

### Function Signature

```c
long pthFactor(long n, long p) {
    // Your code here
}
```

### Evaluation Criteria

- ✓ Correctness of the solution
- ✓ Efficiency (O(√n) expected)
- ✓ Proper memory management
- ✓ Handling of edge cases

---

## 🧪 Question 2: Top Scoring Students (MySQL)

### Problem Statement

Write a SQL query to retrieve the ID and NAME of the **three highest-scoring students**, sorted by score in descending order. For students with matching scores, sort by ID in ascending order.

### Schema

**STUDENT Table:**

| Column | Type    | Description              |
|--------|---------|--------------------------|
| ID     | Integer | Unique ID (Primary Key)  |
| NAME   | String  | Student name             |
| SCORE  | Float   | Math score               |

### Sample Input

| ID | NAME  | SCORE |
|----|-------|-------|
| 1  | Bob   | 50.0  |
| 2  | John  | 65.5  |
| 3  | Harry | 45.0  |
| 4  | Dick  | 85.0  |
| 5  | Dev   | 25.0  |
| 6  | Sid   | 98.0  |
| 7  | Tom   | 90.0  |
| 8  | Julia | 70.5  |
| 9  | Erica | 81.0  |
| 10 | Jerry | 85.0  |

### Expected Output

| ID | NAME |
|----|------|
| 6  | Sid  |
| 7  | Tom  |
| 4  | Dick |

### Evaluation Criteria

- ✓ Correct sorting (primary: SCORE DESC, secondary: ID ASC)
- ✓ Proper use of LIMIT clause
- ✓ Clean and readable query syntax

---

## 🧪 Question 3: Top Articles API (C++)

### Problem Statement

Implement a function that retrieves and ranks the top articles from the HackerRank Articles API.

### API Endpoint

```
https://jsonmock.hackerrank.com/api/articles?page=<pageNumber>
```

### Requirements

- **Pagination:** Fetch all pages of article data using the `total_pages` field from the API response.
- **Article Name Determination:**
  - If `title` is not null, use `title`
  - Otherwise, if `story_title` is not null, use `story_title`
  - If both are null, skip the article
- **Sorting:**
  - **Primary:** Decreasing by `num_comments` (treat null as 0)
  - **Secondary:** Alphabetically decreasing by article name
- **Return:** The top `limit` article names

### Function Signature

```cpp
vector<string> topArticles(int limit) {
    // Your code here
}
```

### Sample

**Input:** `limit = 2`  
**Output:**
```
UK votes to leave EU
F.C.C. Repeals Net Neutrality Rules
```

### JSON Response Structure

```json
{
  "page": 1,
  "per_page": 10,
  "total": 100,
  "total_pages": 10,
  "data": [
    {
      "title": "Article Title",
      "story_title": "Story Title",
      "num_comments": 50,
      ...
    }
  ]
}
```

### Evaluation Criteria

- ✓ Correct HTTP request handling and pagination
- ✓ Accurate JSON parsing
- ✓ Proper implementation of sorting logic
- ✓ Handling of null/edge cases
- ✓ Clean, efficient code structure

---

## 📤 Submission Guidelines

### Folder Structure

Create a folder with the following naming convention:

```
Annex_Assessment_<YourName>/
├── pth_factor.c
├── top_students.sql
└── top_articles.cpp
```

Replace `<YourName>` with your full name (e.g., `Annex_Assessment_John_Doe`).

### Submission Steps

1. Create the folder structure as specified above
2. Add your three solution files
3. Compress the folder as a `.zip` file
4. Upload to the link provided in your email

---

## ✅ Pre-Submission Checklist

Before submitting, please verify:

- [ ] All code compiles without errors or warnings
- [ ] All solutions have been tested with the provided sample inputs
- [ ] Edge cases have been considered and handled properly
- [ ] **No AI-generated code is present in your submission**
- [ ] All three required files are included in the submission
- [ ] Folder structure follows the naming convention

---

## 📞 Support & Clarifications

If you have any questions about the assessment, please reach out to the Talent Acquisition Team at your earliest convenience. We're happy to clarify any ambiguities.

**Best of luck with your assessment!** We look forward to reviewing your solutions.

---

**Annex Technologies Limited**  
*Talent Acquisition Team*
