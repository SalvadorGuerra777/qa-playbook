# Bug report template

**Title:** [Where] [what happens] [when], e.g. "Checkout: total ignores discount when the cart has one item"

| Field | Value |
|---|---|
| Environment | URL / build / app version |
| Platform | Browser + version, OS, device |
| Severity | Critical / High / Medium / Low (see table below) |
| Priority | Set with the product owner |
| Found in | Story / test case ID |
| Reproducible | Always / Intermittent (x of y tries) / Once |

## Steps to reproduce

1.
2.
3.

## Expected result

What should happen, with the source: acceptance criteria, API docs, previous behaviour.

## Actual result

What happens. Exact error messages, status codes and values.

## Evidence

- Screenshot or video
- Request and response (`curl` or HAR), with tokens and personal data removed
- Logs or console errors
- Query and result if it is a data issue

## Notes

Workaround, first build where it appears, related tickets.

---

## Severity guide

| Severity | Meaning | Example |
|---|---|---|
| Critical | Data loss, security issue, money moved wrongly, or main flow blocked for everyone | Payment charged twice |
| High | Main feature broken with no reasonable workaround | Users can't download statements |
| Medium | Feature broken but there is a workaround, or a minor flow is blocked | Filter resets after going back |
| Low | Cosmetic or wording issue | Misaligned label |

## Before sending

- [ ] Reproduced it again on the latest build
- [ ] Searched Jira for duplicates
- [ ] Steps work for someone who has never seen the feature
- [ ] One bug per report
- [ ] No passwords, tokens or real customer data in the evidence
