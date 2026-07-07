# User ID Controlled by Request Parameter, with Unpredictable User IDs

**Category:** Access Control (IDOR)
**Difficulty:** Practitioner

---

## Objective
Exploit the same IDOR pattern as the basic version, but where user IDs are non-sequential/unpredictable (e.g. GUIDs), requiring the ID to be leaked from elsewhere first.

## Vulnerability
Same core flaw — no server-side ownership check on the user ID parameter — but this time IDs can't simply be incremented/guessed. The application relies on the assumption that IDs are "unguessable" as an implicit security control.

## Technique
1. Searched the application for any place another user's ID might be disclosed — e.g. a comments section, user listing, API response, or referral link — since sequential guessing wasn't viable.
2. Found a leaked user ID in a location the app didn't intend to expose it (a common pattern: IDs leaking via other features like "view profile" links from a public post).
3. Used the leaked ID in the vulnerable parameter to access that user's account data.

## Key Takeaway
Relying on IDs being "hard to guess" is the same obscurity trap as unpredictable URLs — it fails the moment an ID is exposed anywhere else in the application (which is very common). The only real fix is the same as before: enforce ownership checks server-side, regardless of how unguessable the identifier is.
