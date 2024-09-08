# Appointment

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.162.26 
PING 10.129.162.26 (10.129.162.26) 56(84) bytes of data.
64 bytes from 10.129.162.26: icmp_seq=1 ttl=63 time=207 ms
64 bytes from 10.129.162.26: icmp_seq=2 ttl=63 time=480 ms
^C
--- 10.129.162.26 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 207.383/343.731/480.080/136.348 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -O -sV -Pn 10.129.162.26 
[sudo] password for kali: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-08 11:18 EDT
Nmap scan report for 10.129.162.26
Host is up (0.027s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=9/8%OT=80%CT=1%CU=43965%PV=Y%DS=2%DC=I%G=Y%TM=66DDC
OS:044%P=x86_64-pc-linux-gnu)SEQ(SP=107%GCD=1%ISR=10C%TI=Z%CI=Z%II=I%TS=A)O
OS:PS(O1=M552ST11NW7%O2=M552ST11NW7%O3=M552NNT11NW7%O4=M552ST11NW7%O5=M552S
OS:T11NW7%O6=M552ST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)E
OS:CN(R=Y%DF=Y%T=40%W=FAF0%O=M552NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F
OS:=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5
OS:(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z
OS:%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=
OS:N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%
OS:CD=S)

Network Distance: 2 hops

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 25.63 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ gobuster dir -w /usr/share/wordlists/dirb/common.txt -u 10.129.162.26 
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.129.162.26
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 278]
/.hta                 (Status: 403) [Size: 278]
/.htpasswd            (Status: 403) [Size: 278]
/css                  (Status: 301) [Size: 312] [--> http://10.129.162.26/css/]
/fonts                (Status: 301) [Size: 314] [--> http://10.129.162.26/fonts/]
/images               (Status: 301) [Size: 315] [--> http://10.129.162.26/images/]
/index.php            (Status: 200) [Size: 4896]
/js                   (Status: 301) [Size: 311] [--> http://10.129.162.26/js/]
/server-status        (Status: 403) [Size: 278]
/vendor               (Status: 301) [Size: 315] [--> http://10.129.162.26/vendor/]
Progress: 4614 / 4615 (99.98%)
===============================================================
Finished
===============================================================
```

![image](https://github.com/user-attachments/assets/0a55b656-b1af-433a-815d-3514c375f419)

![image](https://github.com/user-attachments/assets/636bf0b5-ab23-493f-9364-3dfb2bba7032)



