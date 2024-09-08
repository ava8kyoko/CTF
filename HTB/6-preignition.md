# Pregnition

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.204.154
PING 10.129.204.154 (10.129.204.154) 56(84) bytes of data.
64 bytes from 10.129.204.154: icmp_seq=1 ttl=63 time=617 ms
64 bytes from 10.129.204.154: icmp_seq=2 ttl=63 time=24.7 ms
64 bytes from 10.129.204.154: icmp_seq=3 ttl=63 time=24.4 ms
^C
--- 10.129.204.154 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 24.360/222.147/617.347/279.448 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sS -sV 10.129.204.154 
[sudo] password for kali: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 20:10 EDT
Nmap scan report for 10.129.204.154
Host is up (0.028s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.14.2

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.43 seconds
```

![image](https://github.com/user-attachments/assets/3e07eec4-f743-48b2-94da-cd7a308da806)


```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo gobuster dir -x php -w /usr/share/wordlists/dirb/common.txt -u 10.129.40.219
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.129.40.219
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
/admin.php            (Status: 200) [Size: 999]
/admin.php            (Status: 200) [Size: 999]
Progress: 9228 / 9230 (99.98%)
===============================================================
Finished
===============================================================
```

![image](https://github.com/user-attachments/assets/8b7c45e4-e766-4883-b783-e5c51f0ae7f9)


admin:admin









