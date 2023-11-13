---
aliases:
  - Cisco Discovery Protocol
tags:
  - defs_ccna
dg-publish: true
---
#### CDP
- **Cisco Discovery Protocol** is a [[Layer 2|Layer 2]] protocol to discover directly-connected Cisco devices
	- CDP messages are not forwarded to other devices
- Enabled by default on most Cisco equipment
- It is a closed-protocol similar to [[LLDP]], but provides additional information on VLAN Trunking Protocol [[VTP]]
- Messages are sent periodically to [[Multicast Address]] `0100.0ccc.cccc`
- Sends advertisements every *60 seconds* by default, compared to LLDP's 30 seconds
	- If a message isn't received from a neighbor within *180 seconds (CDP hold time)*, the neighbor is removed from the CDP neighbor table
- CDP is enabled and configured globally, but can also be enabled per interface

### CDP Commands
#### Show commands
1. `sho cdp`
	1. Shows CDP timer
	2. CDP hold time
	3. Which version is enabled
2. `show cdp traffic`
	1. Packets sent and received, and their version
3. `show cdp interface`
	1. Information about all interfaces
4. `show cdp neighbors`
	1. Shows host name
	2. local interface (not the neighbor)
	3. hold time
	4. Capability (basically what kind of device)
		1. R = routing
			1. A layer 3 switch will have "R" as a capability
		2. S = switching
	5. Platform
		1. Device model number
	6. Neighbor port ID
5. `show cdp neighbors detail`
	1. Software version
	2. Interfaces
		1. "Interface" is the local interface
		2. "*Port ID* (Outgoing Port)" is the *NEIGHBOR interface*
	3. VTP information
	4. IP address
6. `show cdp entry <device name, e.g. R2>`
	1. Same as neighbors detail, but for a specific entry

#### CDP Configuration Commands
1. `config# <no> cdp run`
	1. Run/Disable CDP globally
2. `config-if# <no> cdp enable`
	1. Enable/disable CDP on an interface
3. `config# cdp <timer, holdtime, advertise-v2>
	1. Modify the timer, hold time, or version




# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-2-3 
### Contributors

### Sources


