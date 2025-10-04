**Bug:** I was able to buy an old product that's no longer available.

## Steps
Look for the Christmas Special Product (is the product name given on the challenge description)

1. Go to the DB schema injection URL:
localhost:3000/rest/products/search?q=')) UNION SELECT sql,'2','3','4','5','6','7','8','9' FROM sqlite_master-- 
2. Right Click then click Inspect Element
3. Go to Sources tab then search for 'Christmas'
4. Go to the Christmas text, look for the id, and copy it (or just remember it) (id:10)
Now with Burpsuite
5. Go back to localhost:3000/#/search 
6. On Burpsuite Proxy tab, turn on Intercept
7. Click Add to Basket on any product
8. Then on Burpsuite, click Forward, look at Request section and you will see ProductId at the bottom part of the code.
9.  Right click the code and click Send to Repeater
10.  On Burpsuite's Repeater tab, go to the bottom of Request Section and change the ProductId to the id of the Christmas Product (ProductId": 10,)
11.  Click Send 
12.  Going back to Juice Shop, click Your Basket, and you will see the Christmas Product there.
13.  Click Checkout, then Select and Address, Delivery Speed, and Payment Options. Lastly, click Place your order and pay.

## Why this happened:
This happened because the DB Schema is exposed through SQL Injection and we found some old unavailable products written there that was not removed. 
It's still stored in the database. 

