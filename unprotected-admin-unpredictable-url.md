# Unprotected Admin Functionality with Unpredictable URL

**Category:** Access Control
**Difficulty:** Apprentice

---

## Objective
Locate an admin panel hidden behind a non-guessable URL, then access it without any real permission check in place.

## Vulnerability
Same underlying flaw as the basic unprotected admin functionality lab — no server-side access control — but this time the developers tried to compensate by making the admin URL hard to guess rather than actually protecting it.

## Technique
1. Reviewed the page source and other disclosure points (e.g. robots.txt, JS files, page comments) to find the obfuscated admin URL.
2. Found the admin path leaked in a client-side location.
3. Navigated directly to it and accessed admin functionality with no further check.

## Key Takeaway
"Security through obscurity" is not security. An unguessable URL only raises the bar for casual discovery — it does nothing against anyone who checks client-side code, JS bundles, or common disclosure sources. Real protection requires an actual authorization check on the server for every sensitive endpoint.
