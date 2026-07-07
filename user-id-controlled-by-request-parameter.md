# User ID Controlled by Request Parameter

**Category:** Access Control (IDOR)
**Difficulty:** Apprentice

---

## Objective
Access another user's account information by modifying a user ID parameter in the request.

## Vulnerability
An Insecure Direct Object Reference (IDOR) — the application uses a client-supplied user ID (e.g. in the URL or a request parameter) to fetch account data, without confirming that the requesting user is actually authorized to view that specific account.

## Technique
1. Logged in as my own low-privilege test account and located the account/profile endpoint.
2. Noted the URL/parameter contained my own user ID (e.g. `?id=105`).
3. Changed the ID to a different value (e.g. `?id=106`) directly in the browser/Burp Repeater.
4. Successfully retrieved another user's account data with no ownership check performed.

## Key Takeaway
Any endpoint that accepts an ID referencing a specific record (user, order, document, etc.) must verify server-side that the currently authenticated user actually owns or has permission to access that specific record — not just that they're logged in at all.
