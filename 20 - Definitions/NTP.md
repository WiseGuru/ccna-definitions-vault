---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### NTP
- *Network Time Protocol (NTP)* is a protocol to synchronize time and calendar between devices, since manually configured clocks will drift over time
	- NTP and Cisco use UTC by default, so the time zone must be set locally
	- There a certain amount of inaccuracy allowed depending on proximity to NTP Server (1millisecond for same LAN, 50ms over the WAN)
- NTP Communicates over UDP 123
##### NTP Modes
- Cisco devices can act in one or more three NTP modes
	- *Server mode*
		- Issue time to clients
	- *Client mode*
		- Clients request time from servers
	- *Symmetric active mode*
		- Two peer devices (in the same *stratum*) will help keep each other synchronized
##### NTP Stratum
- The distance between *NTP Servers* and the original reference clock is called the **stratum**
	- *Reference clocks* (atomic clocks or GPS clocks) are *Stratum 0*
		- They are the original time sources
	- *Stratum 1* NTP servers are called *Primary servers* and get their time from the *reference clocks*
	- *Stratum 2* from *Stratum 1* And so on down the list
		- *Stratum 2 and above* servers are called *secondary servers* and they operate in both server mode and client mode
	- Anything beyond *Stratum 15* is considered unreliable, and cannot be an NTP

##### Cisco Clocks
- **Clock** is a software clock, and **Calendar** is a hardware clock
	- *Clock* and *Calendar* are configurable in *privileged exec mode*
	- Default time is in UTC
- Time zone and *NTP* must be configured in *global config mode*



### Commands
#### NTP Commands
1. `config# ntp server <IP address>`
	1. Adds NTP server addresses to the associations table
2. `config# ntp source <interface>`
	1. Configured the interface that NTP messages are programmed to send and receive from
	2. Best practice to use Loopback interfaces, since they are not depending on the status of a physical interface
3. `# show ntp associations`
	1. Shows all servers the NTP client is configured to connect to
	2. `*` indicates the server it is syncing with
	3. `+` indicates a server that *may* be synced with
	4. `~` indicates a configured (vs. dynamic?) association
4. `# show ntp status`
	1. Clock synchronized or not
	2. Stratum level
	3. NTP server (reference) address
5. `config# ntp update-calendar`
	1. Keeps the hardware Calendar up to date
6. `config# ntp master <stratum level>`
	1. Sets an NTP Server to act as a "Master" server on the network
	2. The associated address will be a Loopback *address* (NOT *Loopback interface*) for the local device
	3. Default stratum level is **8**
		1. The *loopback address (not interface)* is assigned a stratum of *7*
7. `config# ntp peer <IP address>`
	1. Configures a device as a candidate on the associations table
##### NTP Authentication
1. `config# ntp authenticate`
	1. Enable NTP authentication
2. `config# ntp authentication-key <key number> md5 <key>`
	1. *key numbers* must match between authenticating devices
	2. *key* is a custom password
3. `config# ntp trusted-key <key number>`
	1. Specifies which authentication keys from clients are trusted
4. `config# ntp [server|peer] <ip address> key <key number>`
	1. Identifies which key to use with which server or peer
	2. This command is only run on the client
#### Calendar (hardware clock)
1. `# show calendar`
	1. Show hardware clock config
2. `# calendar set <time> <day> <month> <year>`
	1. Set the hardware clock
#### Clock (software clock)
1. `# show clock <detail>`
	1. Default timezone is UTC
	2. An `*` at the beginning of the output indicates that the time is not considered authoritative/accurate
	3. Detail shows the source, such as hardware calendar, user config, or NTP
2. `# clock set <time> <day> <month> <year>`
	1. Manually set the clock time and date
3. `# clock update-calendar`
	1. Synchronize the hardware Calendar to the Clock time
4. `# clock read-calendar`
	1. Synchronize the software Clock to the hardware Calendar time
5. `config# clock timezone <name for timezone> <hours offest> <minutes offset>`
	1. Name does not have to match actual timezone
6. `config# clock summer-time <word> <date/recurring>`
	1. Word is local name for Daylight Savings time
	2. Configurations (not in Packet Tracer, maybe not important)





# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
