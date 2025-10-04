**Vulnerability:** I was able to view another user's basket !

## Steps
1. Login to Juice Shop
2. Right click then click Inspect Element 
3. Go to Your Basket
4. Go to the Network tab, then on Network tab, go to response tab.
5. See the id (first one) then click Edit and Resend to change that id number into a different one.
6. Once you've edited it, click send.

## Why this happened:
This worked because the application did not check that the requested basket belonged to the user who is currently using it. 
It only fetched a basket based on the ID provided by the user (it failed to verify the ownership).

## How to fix:
- When fetching a basket, check that 'basket.ownerId == loggedInUser.id' to enforce authorization on the server side.
