## Recap

* You'll get the password in level5. it's `aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1`

## Problem 

Username: natas6
URL:      http://natas6.natas.labs.overthewire.org

![image-20201001211513676](https://i.imgur.com/xaTfNoN.png)

## Solution

* In *View sourcecode*:

```php
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas6", "pass": "<censored>" };</script></head>
<body>
<h1>natas6</h1>
<div id="content">

<?

include "includes/secret.inc";

    if(array_key_exists("submit", $_POST)) {
        if($secret == $_POST['secret']) {
        print "Access granted. The password for natas7 is <censored>";
    } else {
        print "Wrong secret";
    }
    }
?>

<form method=post>
Input secret: <input name=secret><br>
<input type=submit name=submit>
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

* We know this php include `"includes/secret.inc";`, So we go to this site.
  ```php
  <?
  $secret = "FOEIUWGHFEEUHOFUOIU";
  ?>
  ```

  * You'll find the secret.

* Next, input secret in input text.

  ![image-20201002040938011](https://i.imgur.com/7FBzKsc.png)
  * You'll find the key.`7z3hEENjQtflzgnT29q7wAvMNfZdh0i9`