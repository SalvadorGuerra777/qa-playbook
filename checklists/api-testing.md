# API testing checklist

Used in [api-contract-testing](https://github.com/SalvadorGuerra777/api-contract-testing) and the API project of [playwright-ui-api-tests](https://github.com/SalvadorGuerra777/playwright-ui-api-tests).

## Contract

- [ ] Status code for success matches the docs (200, 201, 204)
- [ ] Response body matches the JSON schema: required fields, types, no unexpected nulls
- [ ] `Content-Type` header is correct
- [ ] Response time is within the agreed limit

## Input validation

- [ ] Missing required fields → `400` with a useful message, never `500`
- [ ] Wrong types (string instead of number, invalid date) → `400`
- [ ] Boundary values: empty string, 0, negative, maximum length, one over the maximum
- [ ] Special characters and accents are stored and returned unchanged (José Peña, O'Neil)
- [ ] Extra unknown fields are ignored or rejected, as documented

## Auth and permissions

- [ ] No token → `401`
- [ ] Invalid or expired token → `401`
- [ ] Valid token without permission for the resource → `403`
- [ ] Wrong credentials → `401`, not `200` with an error body
- [ ] A user can't read or change another user's data by changing the id in the URL
- [ ] Tokens and passwords never appear in responses or logs

## Resources

- [ ] Create → read returns the same data
- [ ] Update → read shows the change; partial update doesn't wipe other fields
- [ ] Delete → read returns `404`
- [ ] Unknown id → `404`
- [ ] Creating the same thing twice behaves as documented (duplicate or `409`)

## Lists and search

- [ ] Pagination metadata is correct (total, page, per page) and the last page is not empty
- [ ] Filters and search return only matching items
- [ ] Search with no matches returns an empty list, not an error
- [ ] Sorting is stable and in the requested order

## Automation notes

- Chain requests with variables (create → use the returned id), never hard-coded ids from a shared environment.
- Clean up what the tests create, or use unique data per run.
- Keep credentials in environment files or CI secrets, never in the collection.
