**Vulnerability:** I saw a code sandbox which was not available on the navigation on the website !!!

## Steps
1. Go to Juice Shop
2. Right click and click Inspect Element
3. Press Ctrl+Shift+F for global search and type ' sandbox '
4. Look for something like ' path: '
5. Copy the path (web3-sandbox) and append to the application URL using hash route. So it becomes http://localhost:3000/#/web3-sandbox 
6. Press Enter

## Why this happened:
- The developers had forgotten to remove the route web3-sandbox on frontend code. 
- They must remove it or restrict access to authorized users only.
