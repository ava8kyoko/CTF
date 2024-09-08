# Synced

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.228.242
PING 10.129.228.242 (10.129.228.242) 56(84) bytes of data.
64 bytes from 10.129.228.242: icmp_seq=1 ttl=63 time=25.3 ms
64 bytes from 10.129.228.242: icmp_seq=2 ttl=63 time=32.2 ms
64 bytes from 10.129.228.242: icmp_seq=3 ttl=63 time=26.6 ms
^C
--- 10.129.228.242 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2017ms
rtt min/avg/max/mdev = 25.257/28.015/32.184/2.998 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ rsync rsync://10.129.228.242
public          Anonymous Share
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ rsync rsync://10.129.228.242/public
drwxr-xr-x          4,096 2022/10/24 18:02:23 .
-rw-r--r--             33 2022/10/24 17:32:03 flag.txt
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ rsync rsync://10.129.228.242/public    
drwxr-xr-x          4,096 2022/10/24 18:02:23 .
-rw-r--r--             33 2022/10/24 17:32:03 flag.txt
                                                                                                          
┌──(kali㉿kali)-[~/Downloads]
└─$ rsync rsync://10.129.228.242/public/flag.txt
-rw-r--r--             33 2022/10/24 17:32:03 flag.txt
                                                                                                          
┌──(kali㉿kali)-[~/Downloads]
└─$ rsync rsync://10.129.228.242/public/flag.txt ./
                                                                                                          
┌──(kali㉿kali)-[~/Downloads]
└─$ ls
10.129.1.14  flag.txt  lab_avakyoko.ovpn  starting_point_avakyoko.ovpn  worknotes.txt
                                                                                                          
┌──(kali㉿kali)-[~/Downloads]
└─$ cat flag.txt 
72eaf5344ebb84908ae543a719830519
```
