# Web UI testing checklist

## Forms

- [ ] Required fields show a clear message when empty
- [ ] Field limits: minimum, maximum, one over the maximum
- [ ] Invalid formats (email, phone, dates) are rejected with a message next to the field
- [ ] Submitting twice quickly doesn't create two records
- [ ] Data typed by the user is kept after a validation error
- [ ] Leading and trailing spaces are handled (trimmed or rejected)

## Navigation and state

- [ ] Back and refresh during a flow don't lose or duplicate data
- [ ] Deep links work, and protected pages redirect to login when there is no session
- [ ] After logout, the back button doesn't show private data
- [ ] Session timeout shows a message and keeps the user's place when possible

## Data shown

- [ ] Values match the API or the database (prices, totals, dates), not only "something is displayed"
- [ ] Empty states: no results, no items, first-time user
- [ ] Long names and large numbers don't break the layout
- [ ] Dates, currency and decimals use the expected format

## Errors

- [ ] Server errors show a friendly message, not a stack trace
- [ ] Slow or failed requests show loading and retry states

## Compatibility and accessibility

- [ ] Latest Chrome, Firefox, Edge and Safari (or the browsers the analytics show)
- [ ] Mobile width: no horizontal scroll, buttons reachable
- [ ] Keyboard only: tab order makes sense, focus is visible, forms can be submitted
- [ ] Images have alt text and inputs have labels

## Automation notes

- Locate elements by test ids or roles, not CSS classes or text that changes.
- Wait for a condition (a response, an element state), never a fixed sleep.
- Each test creates or selects its own data and doesn't depend on another test's result.
