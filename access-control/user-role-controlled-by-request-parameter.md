# User Role Controlled by Request Parameter

**Category:** Access Control
**Difficulty:** Apprentice

---

## Objective
Escalate privileges from a normal user to admin by manipulating a role value sent in the request.

## Vulnerability
The user's role (e.g. `admin` vs `user`) was passed as a client-controlled parameter (such as a cookie or hidden form field) rather than being determined and verified server-side from the authenticated session.

## Technique
1. Logged in as a low-privilege user and intercepted the request using Burp Suite.
2. Identified a parameter/cookie holding the role value (e.g. `role=user`).
3. Modified the value to `role=admin` and replayed the request via Burp Repeater.
4. Gained admin-level access as a result of the server trusting the client-supplied role.

## Key Takeaway
Never trust role or permission data that originates from the client. Roles and permissions must be derived server-side from the authenticated session/user record, never read directly from a request parameter, cookie, or hidden field the client can modify.
