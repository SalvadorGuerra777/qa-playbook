# How I approach testing

The general strategy I apply to a new feature or project. Each team and product changes the details.

## 1. Start from risk

Before writing test cases I ask:

- Who uses this and what happens to them if it fails?
- Does it move money, change data that others rely on, or expose personal information?
- What changed, and what else reads or writes the same data?
- Where have defects appeared before?

High-risk areas get more test cases, negative and boundary cases, and automated regression. Low-risk areas get a quick check or an exploratory session.

## 2. Test at the lowest level that can find the bug

| Level | Good for | Example |
|---|---|---|
| Data (SQL) | Totals, duplicates, broken references, values outside a valid range | [sql-data-quality-checks](https://github.com/SalvadorGuerra777/sql-data-quality-checks) |
| API | Business rules, validation, status codes, auth | [api-contract-testing](https://github.com/SalvadorGuerra777/api-contract-testing) |
| UI | Main user flows, what the user sees, UI and API agreeing | [pytest-selenium-framework](https://github.com/SalvadorGuerra777/pytest-selenium-framework), [playwright-ui-api-tests](https://github.com/SalvadorGuerra777/playwright-ui-api-tests) |
| Manual / exploratory | New features, usability, things that are hard to automate | [exploratory charter](../templates/exploratory-charter.md) |

Most checks belong at API and data level: they are fast and stable. UI tests cover the flows a user really goes through, not every validation rule.

## 3. What I automate

Good candidates:

- Main flows that run in every regression
- Checks with many data combinations (data-driven tests)
- Bugs that escaped once, so they don't come back
- Setup steps that slow down manual testing (creating users, data)

Not worth it (yet):

- Features that are still changing every sprint
- One-time checks
- Visual judgement and usability

## 4. Test design techniques

- **Equivalence classes:** one value per group that behaves the same (valid, invalid, empty).
- **Boundary values:** the limit, one below, one above.
- **Decision tables:** for rules with several conditions (role × account status × amount).
- **State transitions:** for flows with statuses (pending → approved → paid), including invalid transitions.
- **Error guessing:** double submits, refresh mid-flow, special characters, timeouts.

## 5. Working with the team

- Review acceptance criteria during refinement and ask about edge cases before development starts.
- Review automation code in merge requests like any other code: readable, no fixed waits, no shared data.
- Report defects with clear steps and evidence ([template](../templates/bug-report.md)), and agree on severity with the product owner.
- Share a short test summary before release ([template](../templates/test-summary-report.md)), including what was not tested.

## 6. Testing features that use an LLM

Outputs are not exact, so instead of assertions on text:

- A labeled dataset with real-looking inputs, including edge cases and prompt injection attempts
- Code-based graders for what can be checked (labels, format, forbidden content)
- Pass-rate thresholds per grader, with 100% for safety rules
- Deterministic tests for the code around the model (parsing, error handling)

Example: [llm-eval-testing](https://github.com/SalvadorGuerra777/llm-eval-testing).
