# Regression and release checklist

## Choosing what to regress

Not everything gets retested every release. I pick by:

1. **What changed:** the stories in the release and the modules they touch (check the merge requests, not only the ticket).
2. **What depends on it:** shared components, APIs used by other screens, database tables read by reports.
3. **What hurts most if it breaks:** login, money movement, data that customers or auditors see.
4. **What broke before:** areas with recent defects.

The automated suite covers the stable main flows on every build. Manual regression goes to what changed and what the suite doesn't cover.

## Before testing

- [ ] Release notes / list of tickets in the build
- [ ] Build deployed to the test environment, version confirmed
- [ ] Smoke test passed (app loads, login, one main flow)
- [ ] Test data reset or created

## During testing

- [ ] Automated regression green in CI (failures checked, not only rerun)
- [ ] Every story in the release tested against its acceptance criteria
- [ ] Fixed defects retested, plus the area around the fix
- [ ] Manual regression for the areas picked above
- [ ] Integrations checked end to end (APIs, files, external services)
- [ ] Data checks: totals, duplicates, no orphan records

## Sign-off

- [ ] No open critical or high defects, or each one accepted by the product owner
- [ ] Known issues documented for support
- [ ] Test summary sent ([template](../templates/test-summary-report.md))

## After release

- [ ] Smoke test in production, if the team allows it
- [ ] Watch errors and support tickets for the first hours
- [ ] Add regression tests for any defect that escaped
