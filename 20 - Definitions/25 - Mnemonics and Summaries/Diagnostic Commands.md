---
dg-publish: true
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
1. `ping [destination IP]` sends [[ICMP]] echo requests to a destination IP address
2. A quick way to test *two-way [[Layer 3]] connectivity* between hosts
	1. The *ICMP echo request* must be able to reach the destination, and the *ICMP echo reply* must be able to return

## Traceroute
1. A step further than Ping, `traceroute [destination IP]` sends [[UDP]] datagrams with *incrementing [[TTL]]* values to a destination IP, with a default target *UDP port 33434*
2. Each hop replies, and the route to the destination IP is mapped out.

## Telnet
1. While [[Telnet]] is not secure for data transmission, it can be used to test [[Layer 4]] connectivity between devices and verify *open ports* with just `telnet [host name or IP] [port number]`
	1. Requires almost no setup, and the receiving device doesn't need to support it
	2. You will receive a message stating whether the message was successful or nor


# Debug and Logging Information

## `debug [opt]``
1. The **debug** command shows real-time logging information directly in the console
	1. `undebug [opt]` and `undebug all` (or shortened to `u all`) can stem the flow of information



# Host Network Information
Below are sample output commands for the `ping` and `ipconfig/ifconfig` for different host operating systems.

Where applicable, I changed the *code syntax highlighter* to make the output more readable. Nothing really helped with `ifconfig`. 
## Ping Command:

1. **Windows:**
   - **Command:** Open Command Prompt and use the "ping" command.
   - **Example:** `ping google.com`
   - **Output:**
![[Diagnostic Commands-1.png]]

2. **Linux (using Terminal):**
   - **Command:** Open the terminal and use the "ping" command.
   - **Example:** `ping google.com`
   - **Output:**
![[Diagnostic Commands-2.png]]

3. **macOS (using Terminal):**
   - **Command:** Open the terminal and use the "ping" command.
   - **Example:** `ping google.com`
   - **Output:**
![[Diagnostic Commands-3.png]]

## ipconfig/ifconfig Command:

1. **Windows:**
   - **Command:** Open Command Prompt and use the `ipconfig` command.
   - **Example:** `ipconfig`
   - **Output:**
![[Diagnostic Commands-4.png]]

2. **Linux (using Terminal):**
   - **Command:** Open the terminal and use the "ifconfig" command.
   - **Example:** `ifconfig`
   - **Output:**
![[Diagnostic Commands-5.png]]

3. **macOS (using Terminal):**
   - **Command:** Open the terminal and use the "ifconfig" command.
   - **Example:** `ifconfig`
   - **Output:**
![[Diagnostic Commands-6.png]]


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[GitHub - HerrSpace/CCNA-Cheat-Sheet: A comprehensive CCNA CLI reference.](https://github.com/HerrSpace/CCNA-Cheat-Sheet#troubleshoot-basic-networking)
[Cisco Network Troubleshooting for Beginners | Pluralsight](https://www.pluralsight.com/blog/it-ops/cisco-network-troubleshooting)
[ping (networking utility) - Wikipedia](https://en.wikipedia.org/wiki/Ping_(networking_utility))
[traceroute - Wikipedia](https://en.wikipedia.org/wiki/Traceroute)
[Cisco IOS Debug Command Reference](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/debug/command/db-i1-cr-book/db-i1-cr-book_CLT_chapter.html)
