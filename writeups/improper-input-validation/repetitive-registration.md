**Challenge:** Followed the DRY (Don't Repeat Yourself) principle while registering a user.

## Steps
1. Go to Login and click 'Not yet a customer?'
2. In User Registration, input email (e.g: testuser@juiceshop.com)
3. Input Password then Repeat Password. They must both match. (e.g: Password: juiceshop 
Repeat Password: juiceshop)
4. After it matches, click the Password input box and change it into a different password. Don't change the Repeat Password. (e.g:
Password: juiceshop123
Repeat Password: juiceshop)
5. Complete the Security Question and Answer.
6. Click Register

## Why it happened:
- The  account is successfully created, even though the two password fields are different.
- The application only checks if the Repeat Password matches the password at the moment you first type them in.

I found this code on their main.js:
t.Y8G("ngIf", a.repeatPasswordControl.invalid && a.repeatPasswordControl.errors.required),
t.R7$(),
t.Y8G("ngIf", a.repeatPasswordControl.invalid && a.repeatPasswordControl.errors.notSame),

The check is only happening on the *repeatPasswordControl* field.
Nothing re-validates if you later change the original password field after filling in Repeat Password.
It only checks the repeat password against the first password, but not the other way around . 

This means the system can create accounts with mismatched or unexpected passwords.

## How to fix:
- The server should always double check that the two passwords match before creating the account, to make sure users don’t end up with broken or unusable accounts and prevents attackers from bypassing the registration rules
- Don’t validate passwords separately in two places ! Write one validation rule that applies to both fields, and reuse it.
