---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### DHCP Snooping
- *DHCP Snooping* inspects [[DHCP]] packets to prevent networking problems and attacks from rogue DHCP servers
- Compares addresses on the *DHCP Snooping binding* table
	- The *binding* table records the Client's *MAC* address, *IP* address, IP *Lease* time, and *VLAN* to its *interface*
		- ![[DHCP Snooping Binding table-1.png]]
	- [[DAI]] also uses the *Snooping table* in its frame validation
- It identifies ports as *Trusted* or *Untrusted*
	- **Trusted** ports *forward all DHCP* messages without inspection
	- **Untrusted** ports *act on all DHCP* messages
		- *Discard* DHCP *server* messages
		- *Inspect* DHCP *client* messages
			- **Forwards** messages that *match* its configured information on the *DHCP snooping table*, and **discards** messages that *don't match*
				- **Discover/Request** DHCP Messages
					- Check the frame's *source MAC* and the DHCP message's *CH***ADDR** (Client Hardware Address, i.e. the client's MAC address) fields match
				- **Release/Decline** DHCP Messages
					- Check the *source IP* and receiving *interface* match the entry on the *binding* table
- *Rate Limiting*
	- Automatically *disables interfaces* that send more requests than a configured threshold
	- [[Error Disabled]] interfaces can be *manually* or *automatically* returned to service
- DHCP *Option 82* (aka `information option`)
	- Optionally and only sent by *DHCP relay agents* on messages they *forward* to the *DHCP Server*
		- Provides information about *which relay agent* is forwarding the message, the *VLAN*, *interface*, etc.
	- By default, DHCP Snooping *tags all messages* from clients with *option 82*
		- However, [[Layer 2]] Switches **drop** incoming DHCP packets with Option 82 on *untrusted ports* by default
		- Similarly, Cisco Routers acting as DHCP server will drop 
			- Error message keywords:
				- `inconsistent relay information`
				- `relay information option exists, but giaddr is zero`
		- It is therefore important to *disable option 82* when configuring DHCP Snooping
			- `config# no ip dhcp snooping information option`


![[DHCP#DHCP Operations]]



### DHCP Snooping config
1. Enable IP DHCP snooping
	2. `config# ip dhcp snooping`
2. Assign a VLAN to be snooped
	1. `config# ip dhcp snooping vlan <vlan ID>`
3. Disable IP DHCP snooping information
	1. `config# no ip dhcp snooping information option`
4. Trust the server-facing interface
	1. `config-if# ip dhcp snooping trust`
5. Check DHCP snooping table
	1. `#sho ip dhcp snooping binding`
6. Configure DHCP rate limiting
	1. `config-if-range# ip dhcp snooping limit rate <allowed messages per second>`
7. Configure errdisable recovery
	1. `config# errdisable recovery cause dhcp-rate-limit`
	2. `# show errdisable recovery`



# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[Configuring DHCP Snooping - Cisco Systems](https://www.cisco.com/en/US/docs/general/Test/dwerblo/broken_guide/snoodhcp.html#wp1074087)


