## Recap

* You'll get the password in level7. it's `DBfUBfqQG69KvJvJ1iAbMoIpwSNQ9bWe`

## Problem 

Username: natas8
URL:      http://natas8.natas.labs.overthewire.org

* HTML render

![image-20201002042536374](https://i.imgur.com/LM46GPc.png)

* Source Code

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
<script>var wechallinfo = { "level": "natas8", "pass": "<censored>" };</script></head>
<body>
<h1>natas8</h1>
<div id="content">

<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
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

## Solution

* By code , we want:  `3d3d516343746d4d6d6c315669563362` = `bin2hex(strrev(base64_encode(input)))`
  * Reverse the function: hex2bin -> strrev -> base64decode. We use python to do it.

![image-20201002043407186](https://i.imgur.com/Vfc9IJK.png)

* After process, you know the secret: `oubWYf2kBq`, type it in input field, you'll get the token `W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl`.

![image-20201002043455815](https://i.imgur.com/L7d616c.png)