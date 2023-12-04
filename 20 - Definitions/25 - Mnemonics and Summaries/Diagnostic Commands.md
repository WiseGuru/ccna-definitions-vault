---
dg-publish: true
aliases: 
tags: []
---
There are a variety of *Cisco IOS* and *networking* tools you can use for *information gather* and *diagnostics*. I've broken them up into a few groups to make them easier to remember, but there will often be overlap.

# Connected Device Information
If you want to learn anything about a device, the `show` command is what you need. There are many sub-commands that you can use to reveal information about the device, but here are a few basic ones you should be familiar with.

## `show running-config` and `show startup-config`
1. Can be used to compare the entire config *between devices* (or to check for *unsaved changes*)
2. Often a great place to start to gather basic config information.

## `show interfaces`
1. Shows detailed [[Layer 1]] and [[Layer 2]] information about all interfaces or a specific interface
2. Allows use of the `brief` sub-command to summarize information

## `show ip interface`
1. Shows detailed [[Layer 3]] information about all interfaces or a specific interface
2. Can be summarized with the `brief` command
3. Can return IPv6 information with `show ipv6 interface`

## `show ip route`
1. Shows the [[Routing Table]], which detailed *network routes* and how they were learned

## `show cdp neighbors` and `show lldp neighbors`
1. [[CDP]] is enabled by default on Cisco devices, and communicates identifying information between devices
2. This can be very helpful if you don't know which interface a Switch is plugged into, and can help you reconstruct the network topology

## `show ip protocols`
1. Shows the running [[Dynamic Routing Protocols]] on a device, and their configurations

## `show arp`
1. Shows the [[ARP]] entry (i.e., [[IPv4|IP address]] and [[MAC Address]]) for all interfaces


# Network Connectivity
## Ping
1. `ping <destination IP>` sends [[ICMP]] echo requests to a destination IP address
2. A quick way to test *two-way [[Layer 3]] connectivity* between hosts
	1. The *ICMP echo request* must be able to reach the destination, and the *ICMP echo reply* must be able to return

## Traceroute
1. A step further than Ping, `traceroute <destination IP>` sends [[UDP]] datagrams with *incrementing [[TTL]]* values to a destination IP, with a default target *UDP port 33434*
2. Each hop replies, and the route to the destination IP is mapped out.

## Telnet
1. While [[Telnet]] is not secure for data transmission, it can be used to test [[Layer 4]] connectivity between devices and verify *open ports* with just `telnet <host name or IP> <port number>`
	1. Requires almost no setup, and the receiving device doesn't need to support it
	2. You will receive a message stating whether the message was successful or nor


# Debug and Logging Information

## `debug <opt>`
1. The **debug** command shows real-time logging information directly in the console
	1. `undebug <opt>` and `undebug all` (or shortened to `u all`) can stem the flow of information



# Host Network Information
Below are sample output commands for the `ping` and `ipconfig/ifconfig` for different host operating systems.

Where applicable, I changed the *code syntax highlighter* to make the output more readable. Nothing really helped with `ifconfig`. 
## Ping Command:

1. **Windows:**
   - **Command:** Open Command Prompt and use the "ping" command.
   - **Example:** `ping google.com`
   - **Output:**
     ```Python
     Pinging google.com [216.58.200.142] with 32 bytes of data:
     Reply from 216.58.200.142: bytes=32 time=11ms TTL=118
     Reply from 216.58.200.142: bytes=32 time=12ms TTL=118
     Reply from 216.58.200.142: bytes=32 time=10ms TTL=118
     Reply from 216.58.200.142: bytes=32 time=11ms TTL=118

     Ping statistics for 216.58.200.142:
         Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
     Approximate round trip times in milli-seconds:
         Minimum = 10ms, Maximum = 12ms, Average = 11ms
     ```

2. **Linux (using Terminal):**
   - **Command:** Open the terminal and use the "ping" command.
   - **Example:** `ping google.com`
   - **Output:**
     ```Python
     PING google.com (216.58.200.142) 56(84) bytes of data.
     64 bytes from ord30s31-in-f14.1e100.net (216.58.200.142): icmp_seq=1 ttl=118 time=11.1 ms
     64 bytes from ord30s31-in-f14.1e100.net (216.58.200.142): icmp_seq=2 ttl=118 time=10.8 ms
     64 bytes from ord30s31-in-f14.1e100.net (216.58.200.142): icmp_seq=3 ttl=118 time=10.7 ms
     64 bytes from ord30s31-in-f14.1e100.net (216.58.200.142): icmp_seq=4 ttl=118 time=11.0 ms

     --- google.com ping statistics ---
     4 packets transmitted, 4 received, 0% packet loss, time 3003ms
     rtt min/avg/max/mdev = 10.711/10.951/11.164/0.194 ms
     ```

3. **macOS (using Terminal):**
   - **Command:** Open the terminal and use the "ping" command.
   - **Example:** `ping google.com`
   - **Output:**
     ```Python
     PING google.com (216.58.200.142): 56 data bytes
     64 bytes from 216.58.200.142: icmp_seq=0 ttl=118 time=11.751 ms
     64 bytes from 216.58.200.142: icmp_seq=1 ttl=118 time=10.518 ms
     64 bytes from 216.58.200.142: icmp_seq=2 ttl=118 time=10.792 ms
     64 bytes from 216.58.200.142: icmp_seq=3 ttl=118 time=10.763 ms

     --- google.com ping statistics ---
     4 packets transmitted, 4 packets received, 0.0% packet loss
     round-trip min/avg/max/stddev = 10.518/11.206/11.751/0.457 ms
     ```

## ipconfig/ifconfig Command:

1. **Windows:**
   - **Command:** Open Command Prompt and use the `ipconfig` command.
   - **Example:** `ipconfig`
   - **Output:**
	```YAML
	Windows IP Configuration
	
	Ethernet adapter Ethernet:
	
	   Connection-specific DNS Suffix  . : example.com
	   IPv4 Address. . . . . . . . . . . : 192.168.1.100
	   Subnet Mask . . . . . . . . . . . : 255.255.255.0
	   Default Gateway . . . . . . . . . : 192.168.1.1
	
	Wireless LAN adapter Wi-Fi:
	
	   Connection-specific DNS Suffix  . :
	   IPv4 Address. . . . . . . . . . . : 192.168.0.101
	   Subnet Mask . . . . . . . . . . . : 255.255.255.0
	   Default Gateway . . . . . . . . . : 192.168.0.1
	
	Ethernet adapter Bluetooth Network Connection:
	
	   Media State . . . . . . . . . . . : Media disconnected
	   Connection-specific DNS Suffix  . :
	
	Tunnel adapter Teredo Tunneling Pseudo-Interface:
	
	   Connection-specific DNS Suffix  . :
	   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:90d7:1a5b:19f6:3f57:fef2
	   Link-local IPv6 Address . . . . . : fe80::1a5b:19f6:3f57:fef2%12
	   Default Gateway . . . . . . . . . : ::
	```



2. **Linux (using Terminal):**
   - **Command:** Open the terminal and use the "ifconfig" command.
   - **Example:** `ifconfig`
   - **Output:**
```YAML
enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::a00:27ff:fe80:7c5f  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:80:7c:5f  txqueuelen 1000  (Ethernet)
        RX packets 1659  bytes 124899 (124.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 812  bytes 78559 (78.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2  bytes 96 (96.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2  bytes 96 (96.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

3. **macOS (using Terminal):**
   - **Command:** Open the terminal and use the "ifconfig" command.
   - **Example:** `ifconfig`
   - **Output:**
```YAML
     en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether 78:4f:43:2b:81:ae
    inet6 fe80::3f8d:ccff:fe2b:81ae%en0 prefixlen 64 secured scopeid 0x4
    inet 192.168.1.100 netmask 0xffffff00 broadcast 192.168.1.255
    nd6 options=201<PERFORMNUD,DAD>
    media: autoselect
    status: active

en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether 48:d7:05:12:34:56
    inet6 fe80::1c7:11ff:fe44:b3d4%en1 prefixlen 64 scopeid 0x5
    inet 192.168.0.101 netmask 0xffffff00 broadcast 192.168.0.255
    nd6 options=201<PERFORMNUD,DAD>
    media: autoselect
    status: active

lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
    inet6 ::1 prefixlen 128
    inet 127.0.0.1 netmask 0xff000000
    inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1
```



# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[GitHub - HerrSpace/CCNA-Cheat-Sheet: A comprehensive CCNA CLI reference.](https://github.com/HerrSpace/CCNA-Cheat-Sheet#troubleshoot-basic-networking)
[Cisco Network Troubleshooting for Beginners | Pluralsight](https://www.pluralsight.com/blog/it-ops/cisco-network-troubleshooting)
[ping (networking utility) - Wikipedia](https://en.wikipedia.org/wiki/Ping_(networking_utility))
[traceroute - Wikipedia](https://en.wikipedia.org/wiki/Traceroute)
[Cisco IOS Debug Command Reference - Commands I through L - Index [Support] - Cisco](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/debug/command/db-i1-cr-book/db-i1-cr-book_CLT_chapter.html)
