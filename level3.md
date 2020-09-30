## Recap

* You'll get the password in level2. it's `sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14`

## Problem 

Username: natas3
URL:      http://natas3.natas.labs.overthewire.org

![image-20200930225830937](https://i.imgur.com/wPXqjkL.png)

## Solution

F12 (html content):

![image-20200930230105416](https://i.imgur.com/3znwLpF.png)

* `Not even Google will find it this time...`. This implies this website maybe use robots.txt, which disallow the users to find the information through google.
  * Thus, we find the robots.txt, and find out what we got.	

* In http://natas3.natas.labs.overthewire.org/robots.txt:

  ```
  User-agent: *
  Disallow: /s3cr3t/
  ```

  * And we know there's secret folder named s3cr3t, lets dig the file deeper.

* In http://natas3.natas.labs.overthewire.org/s3cr3t:

  * ![image-20200930230912252](https://i.imgur.com/1WPuTWR.png)

* Get users.txt, and find the password!

```
natas4:Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ
```

