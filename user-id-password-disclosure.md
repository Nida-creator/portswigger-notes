# User ID Controlled by Request Parameter, with Password Disclosure

**Category:** Access Control (IDOR)
**Difficulty:** Practitioner

---

## Objective
Escalate a basic IDOR into full account takeover by exposing another user's password through the same vulnerable parameter.

## Vulnerability
The same IDOR flaw as the other user-ID labs, but here the endpoint returns additional sensitive data — including the account's password — when the ID is swapped, rather than just profile/account info.

## Technique
1. Located the vulnerable endpoint returning account details when a user ID parameter is supplied.
2. Modified the ID to reference the target account (e.g. an admin user), as in the earlier IDOR labs.
3. Reviewed the full response body rather than just the visible profile fields — found the account's password included in the raw response data.
4. Used the disclosed password to log in directly as the target user, achieving full account takeover.

## Key Takeaway
IDOR vulnerabilities aren't always "just" information disclosure — depending on what data an endpoint returns, they can escalate directly into full account compromise. This reinforces the importance of reviewing entire API/response bodies during testing, not just the fields rendered in the UI, since sensitive data can be present in a response without being displayed.
