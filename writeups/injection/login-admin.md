**Vulnerability:** I was able to login the admin's account !!!

## Steps
1. Go to Login Page
2. Input ' OR 1=1-- on the email
3. Then just input anything on the password. example:1234
4. Click Login

## Why this happened
The written code on SQL for login uses concatenation like:

const query = "SELECT * FROM Users WHERE email = '" + email + "' AND password = '" + password + "';"; 

when you inject ' OR 1=1--  on the email, it will be considered as part of the SQL code because that's how concatenation (+ email +) works . 

For the code ' OR 1=1 -- :

(') closes the email string so that we can input the SQL code OR 1=1 after it, which makes the whole code mean: 'login to a specific type of email OR true'. Since the boolean 1=1 satisfies the condition, the website will automatically use the first email in the database, which is usually the admin's email. the (--) at the end of the code is syntax for comments which will make the rest of the code after it be disregarded.

## How to fix:
On the SQL login code, replace + email + and + password + into ? placeholder. It will then treat the email and password input into data value instead of it being part of the code. (search usage of parameterized quieries).
