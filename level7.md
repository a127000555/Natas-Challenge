## Recap

* You'll get the password in level6. it's `7z3hEENjQtflzgnT29q7wAvMNfZdh0i9`

## Problem 

Username: natas7
URL:      http://natas7.natas.labs.overthewire.org

![image-20201002041037145](https://i.imgur.com/cBxIxVI.png)

## Solution

* Html source code give us hint.

![image-20201002041413134](https://i.imgur.com/GpmRcOZ.png)

* And we know get param: page can redirect to somewhere.
  * So we just go to http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8
  * You'll get the token. `DBfUBfqQG69KvJvJ1iAbMoIpwSNQ9bWe`

![image-20201002041545958](https://i.imgur.com/yNj2h8b.png)