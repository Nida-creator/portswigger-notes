# Unprotected Admin Functionality

**Category:** Access Control
**Difficulty:** Apprentice

---

## Objective
Identify and access an unprotected admin panel that has no access control check at all.

## Vulnerability
The application exposes admin functionality on a predictable URL (e.g. `/admin`) with no server-side check confirming the requesting user actually has admin privileges. Anyone who navigates directly to the URL gets full access.

## Technique
1. Browsed the site normally as a low-privilege/unauthenticated user.
2. Manually navigated to `/admin` (a common, guessable admin path).
3. Gained full access to admin functionality — no login or role check enforced.

## Key Takeaway
Access control has to be enforced server-side, on every request, regardless of whether the URL is "hidden" or not linked in the UI. If a user can reach the endpoint at all, the server must verify their permission to use it — obscurity is not access control.
