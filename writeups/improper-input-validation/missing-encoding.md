**Bug:** I retrieved the photo of Bjoern's cat in "melee combat-mode" !!!

## Steps
1. Go to the PhotoWall
2. Right-click then Inspect
3. Go to the Network tab
4. Look for: /assets/public/images/uploads/ᓚᘏᗢ-#zatschi-#whoneedsfourlegs-1572600969477.jpg
5. Change the URL to: /assets/public/images/uploads/ᓚᘏᗢ-%23zatschi-%23whoneedsfourlegs-1572600969477.jpg
6. Reload the URL and the cat pic will show up !

## Why it happened:
The browser tried to request the URL, but it stopped at the first #, so it only asked the server for:
/assets/public/images/uploads/ᓚᘏᗢ-

Browsers follow a rule called URL encoding (percent encoding).
Special characters that have meaning in URLs (like #, ?, spaces) must be converted into 'safe codes'.
Each character is represented by % + its ASCII/Unicode code in hexadecimal.
For #, the ASCII code is 23 in hexadecimal, so it becomes %23.

So the fixed URL looks like:
/assets/public/images/uploads/ᓚᘏᗢ-%23zatschi-%23whoneedsfourlegs-1572600969477.jpg

Now the browser requests the whole string as part of the filename, and the server can find the cat photo.

