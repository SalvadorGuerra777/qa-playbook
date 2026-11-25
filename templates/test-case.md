# Test case template

| Field | Value |
|---|---|
| ID | TC-[number] |
| Title | [Action] [expected result], e.g. "Login with a locked account shows the unlock message" |
| Requirement / story | |
| Priority | High / Medium / Low |
| Type | Functional / Negative / Boundary / Regression / Integration |
| Automated | No / Yes (link to test) |

## Preconditions

- User, role and data needed before step 1

## Steps and expected results

| # | Step | Expected result |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

## Test data

| Field | Value | Why this value |
|---|---|---|
| | | e.g. "maximum length (50 chars)" |

## Notes

Anything that makes the case easier to run or explains a non-obvious expected result.

---

## Writing rules I follow

- One behaviour per test case. If the title needs "and", it is probably two cases.
- The expected result is observable: a message, a status code, a value in the database. Not "works correctly".
- Steps say what to do, not how the UI looks ("Submit the form", not "Click the blue button on the right").
- Negative and boundary cases get their own IDs, they are where most defects are.
- For boundary values test the limit, one below and one above (for a 1–50 character field: 0, 1, 50, 51).
- Mark a case as automated only when the automated test checks the same expected results.
