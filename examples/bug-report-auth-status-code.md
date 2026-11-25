# Example: bug report filled in

A real defect found while building [api-contract-testing](https://github.com/SalvadorGuerra777/api-contract-testing), written with the [bug report template](../templates/bug-report.md). Restful Booker is a public practice API, so this one can be shared. Reproduced again on 2026-11-25.

---

**Title:** Auth API: wrong password returns 200 OK instead of 401 Unauthorized

| Field | Value |
|---|---|
| Environment | `https://restful-booker.herokuapp.com` (public demo) |
| Platform | API, any client (checked with curl and Newman) |
| Severity | Medium |
| Found in | `api-contract-testing`, negative auth request |
| Reproducible | Always |

## Steps to reproduce

```bash
curl -i -X POST https://restful-booker.herokuapp.com/auth \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "wrong"}'
```

## Expected result

`401 Unauthorized`. The request has invalid credentials, and that is the status code HTTP defines for failed authentication.

## Actual result

```text
HTTP/1.1 200 OK
{"reason":"Bad credentials"}
```

## Impact

A client that checks only the status code treats the login as successful and continues without a token. To detect the failure the client has to parse the body, which is easy to miss.

## Notes

- The same endpoint returns `200` with a `token` for valid credentials, so status alone can't tell success from failure.
- Related: `POST /booking` with missing required fields returns `500 Internal Server Error` instead of `400 Bad Request`.
- The collection asserts the current behaviour and labels it as a known defect, so a fix shows up as a failing test that needs updating.

## Why medium and not high

Clients still fail later because they get no token, and there is no data loss or security bypass. It would be high if the API returned a token or let the request through.
