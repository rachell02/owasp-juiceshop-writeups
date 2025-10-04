**Vulnerability:** I was able to login Jim's account !!!

## Steps:
1. Go to Login Page
2. Input jim@juice-sh.op'-- on the email
3. Then just input anything on the password. example: 1234
4. Click Login

## Why this happened?:
The written code on SQL for login uses concatenation. 
Example:

const email = "jim@juice-sh.op'--";
const password = "1234";

const query = "SELECT * FROM Users WHERE email = '" + email + "' AND password = '" + password + "';";

## Explanation: 
The ' at the end of jim@juice-sh.op email is for closing the email string, then the -- syntax for putting comments on SQL, meaning the rest of the code after that will be disregarded (because it became a comment). 
This worked because the Input of the user's email and password will be treated as part of the code (because of + email + and + password + concatenation) rather than a separate data value.

## How to fix:
On the SQL login code, replace + email + and + password + into ? placeholder. It will then treat the email and password input into data value instead of it being part of the code. (search usage of parameterized quieries)
