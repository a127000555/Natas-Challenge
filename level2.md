## Recap

* You'll get the password in level1. it's `ZluruAthQk7Q2MqmDeTiUij2ZvWy2mBi`

## Problem

Username: natas2
URL:      http://natas2.natas.labs.overthewire.org

* *There's nothing on this page.*

![image-20200930225202250](https://i.imgur.com/xkLZjRN.png)

## Solution

* You can find this page has strange image: 

	![image-20200930225341707](https://i.imgur.com/i4BU0dy.png)

	* Which let you know there's folder in files/. Let's check what's inside the files/. (Maybe we don't need authority.)

* Goto http://natas2.natas.labs.overthewire.org/files/ :

  * ![image-20200930225611034](https://i.imgur.com/jlynEth.png)

* Boom! there's `users.txt` inside. And the following is what users.txt gave.

  ```
  # username:password
  alice:BYNdCesZqW
  bob:jw2ueICLvT
  charlie:G5vCxkVV3m
  natas3:sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14
  eve:zo4mJWyNj2
  mallory:9urtcpzBmH
  ```

* And we know password is `sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14`