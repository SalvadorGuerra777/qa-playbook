# Flaky test triage

A flaky test passes and fails on the same code. Rerunning until green hides real bugs and makes people stop trusting the suite, so each flaky test gets investigated.

## 1. Confirm it is flaky

- [ ] Run it alone several times (`--repeat-each=10` in Playwright, `pytest --count` with pytest-repeat, or a loop)
- [ ] Run it with the full suite and in parallel, as in CI
- [ ] Compare local and CI results

## 2. Collect evidence from a failed run

- [ ] Error message and the line where it failed
- [ ] Screenshot, video or trace (Playwright trace viewer)
- [ ] Network requests around the failure: status, timing, order
- [ ] Test data used and what other tests ran at the same time

## 3. Common causes

| Cause | Sign | Fix |
|---|---|---|
| Timing / race | Old content still on screen, element "detached" | Wait for the response or the new state, not a fixed time |
| Shared data | Fails only in parallel or after a specific test | Unique data per test, or create and clean up in fixtures |
| Test order | Fails when run alone, or only when run after another test | Remove hidden dependencies between tests |
| Shared account state | Account locked, cart not empty, session expired | Separate accounts for negative tests, reset state before the test |
| Environment | Slow responses, only on CI runners | Check timeouts against measured times, fewer workers on shared demos |
| Real product bug | Same failure under the same conditions | Report it, don't hide it in the test |

## 4. Decide

- Fix the test if the cause is in the test.
- Report a bug if the product behaves inconsistently.
- Quarantine (skip with a reason and a ticket) only if it blocks the pipeline and the fix takes time. Write down why and where it is still covered.

## Real examples from my portfolio

From [playwright-ui-api-tests](https://github.com/SalvadorGuerra777/playwright-ui-api-tests):

- **Stale search results:** the old list stayed on screen until the API answered, so the test read the previous results. Fix: wait for the search response and the new list count.
- **Quantity reset:** the product page reset the quantity field when its API call finished after the test typed. Fix: wait for the product response before typing.
- **Account lockout:** negative login tests used a wrong password on the shared demo account, and after a few runs the API returned `423 Account locked`, breaking the positive test. Fix: negative tests use an email that doesn't exist.
- **CORS preflight:** `waitForResponse` matched the `OPTIONS` request before the `POST`. Fix: filter by method.
- **Page never loads on CI runners only:** passes locally every time. Skipped in CI with the reason in the code; login is still covered by API tests.
