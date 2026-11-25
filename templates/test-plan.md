# Test plan: [feature or release name]

| Field | Value |
|---|---|
| Owner | |
| Sprint / release | |
| Ticket(s) | |
| Status | Draft / In review / Approved |
| Last update | |

## 1. Scope

What changes in this release and which parts of the product it touches.

### In scope

-

### Out of scope (and why)

-

## 2. Risks

List what could go wrong for users, highest impact first. Each risk gets at least one test.

| Risk | Impact | Likelihood | Covered by |
|---|---|---|---|
| Example: a transfer is applied twice after a timeout | High | Medium | TC-012, API suite |

## 3. Approach

| Level | What | Manual / automated | Tool |
|---|---|---|---|
| API | Contracts, status codes, validation, auth | Automated | Postman / Newman, PyTest |
| UI | Main user flows, error messages | Automated + manual | Playwright, Selenium |
| Data | Totals, duplicates, referential integrity | Automated | SQL |
| Exploratory | New behaviour, edge cases, usability | Manual | Session charters |
| Regression | Existing flows touched by the change | Automated suite + manual checklist | CI pipeline |

## 4. Environments and test data

- Environment and build:
- Accounts / roles needed:
- Data to create or reset before testing:
- External services that are mocked or shared:

## 5. Entry criteria

- [ ] Acceptance criteria are written and agreed in the ticket
- [ ] Build is deployed to the test environment and smoke tests pass
- [ ] Test data is ready

## 6. Exit criteria

- [ ] All high-risk test cases executed and passed
- [ ] No open critical or high defects (or accepted by the product owner, with ticket link)
- [ ] Automated regression green in CI
- [ ] Test summary shared with the team

## 7. Schedule

| Activity | Dates | Who |
|---|---|---|
| Test design | | |
| Execution | | |
| Regression | | |
| Sign-off | | |

## 8. Deliverables

- Test cases in the test management tool (TestRail / Xray / Zephyr)
- Defects in Jira, linked to the story
- Test summary report ([template](test-summary-report.md))
