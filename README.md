# qa-playbook

![Docs check](https://github.com/SalvadorGuerra777/qa-playbook/actions/workflows/docs.yml/badge.svg)

The templates, checklists and test strategy I use as a QA engineer. The examples come from my public portfolio projects, so they can be checked and reproduced.

## Contents

### Strategy

- [How I approach testing](strategy/test-strategy.md): risk first, testing at the right level, what to automate, design techniques, LLM features

### Templates

- [Test plan](templates/test-plan.md)
- [Test case](templates/test-case.md), with the writing rules I follow
- [Bug report](templates/bug-report.md), with a severity guide
- [Test summary report](templates/test-summary-report.md)
- [Exploratory session charter](templates/exploratory-charter.md)

### Checklists

- [API testing](checklists/api-testing.md)
- [Web UI testing](checklists/web-ui-testing.md)
- [Regression and release](checklists/regression-and-release.md)
- [Flaky test triage](checklists/flaky-test-triage.md), with real cases from my Playwright project

### Examples

- [Bug report filled in](examples/bug-report-auth-status-code.md): a real defect in a public practice API

## How to use

Copy a template into your ticket, wiki or test management tool (Jira, TestRail, Xray, Zephyr) and delete what doesn't apply. The checklists are starting points, not a full list for every product.

## Related projects

| Project | What it shows |
|---|---|
| [pytest-selenium-framework](https://github.com/SalvadorGuerra777/pytest-selenium-framework) | UI automation with Python, PyTest, Selenium and Page Object Model |
| [playwright-ui-api-tests](https://github.com/SalvadorGuerra777/playwright-ui-api-tests) | UI and API tests with Playwright and TypeScript |
| [api-contract-testing](https://github.com/SalvadorGuerra777/api-contract-testing) | Postman / Newman collection with schema checks and data-driven runs |
| [sql-data-quality-checks](https://github.com/SalvadorGuerra777/sql-data-quality-checks) | SQL data quality checks run with PyTest |
| [llm-eval-testing](https://github.com/SalvadorGuerra777/llm-eval-testing) | Evaluating an LLM feature with a golden dataset and graders |

A CI job lints the Markdown and checks that the links work.
