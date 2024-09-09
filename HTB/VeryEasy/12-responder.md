# Responder

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.249.107
PING 10.129.249.107 (10.129.249.107) 56(84) bytes of data.
64 bytes from 10.129.249.107: icmp_seq=1 ttl=127 time=167 ms
64 bytes from 10.129.249.107: icmp_seq=2 ttl=127 time=26.8 ms
^C
--- 10.129.249.107 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1017ms
rtt min/avg/max/mdev = 26.810/96.753/166.696/69.943 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -p- 10.129.249.107         
[sudo] password for kali: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-08 14:29 EDT
Stats: 0:03:08 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 58.78% done; ETC: 14:34 (0:02:12 remaining)
Nmap scan report for 10.129.249.107
Host is up (0.034s latency).
Not shown: 65532 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
5985/tcp open  wsman
7680/tcp open  pando-pub

Nmap done: 1 IP address (1 host up) scanned in 295.77 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC -sV -p80 10.129.249.107
[sudo] password for kali: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-08 14:44 EDT
Nmap scan report for 10.129.249.107
Host is up (0.70s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.52 ((Win64) OpenSSL/1.1.1m PHP/8.1.1)
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
|_http-server-header: Apache/2.4.52 (Win64) OpenSSL/1.1.1m PHP/8.1.1

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.65 seconds
```
















