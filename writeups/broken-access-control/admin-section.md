**Vulnerability:** I was able to access the administration section of the store

## Steps
1. Go to Login page.
2. SQL injection the admin using ' OR 1=1 --
3. Then go to the administration section.

## Why this happened:
This happened because we were able to SQL Injection to admin's account.

## Mitigation
- Use prepared statements (parameterized queries).
- Don’t concatenate raw input.
