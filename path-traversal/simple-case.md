# File Path Traversal — Simple Case

**Category:** Path Traversal
**Difficulty:** Apprentice

---

## Objective
Read an arbitrary file from the server's filesystem (e.g. `/etc/passwd`) by manipulating a file path parameter.

## Vulnerability
An endpoint accepts a filename/path as user input (e.g. to display an image or document) and passes it to the filesystem without sanitizing directory traversal sequences (`../`), allowing access to files outside the intended directory.

## Technique
1. Identified an endpoint that loads a file based on a user-supplied filename parameter (e.g. `?filename=image.png`).
2. Modified the parameter to traverse up the directory tree and target a sensitive file:
   ```
   ?filename=../../../etc/passwd
   ```
3. The server returned the contents of `/etc/passwd`, confirming the traversal succeeded with no input sanitization in place.

## Key Takeaway
Any endpoint accepting a file path or filename as input must strictly validate and sanitize it — stripping or rejecting `../` sequences, and ideally validating against an allow-list of expected files/directories rather than trusting raw user input to construct filesystem paths.
