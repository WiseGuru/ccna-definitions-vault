---
aliases:
  - Trunking
tags:
  - defs_ccna
dg-publish: true
---
#### Trunk
- A *trunk* interface is a single, physical interface that can route traffic to multiple VLANS
- Functions at [[Layer 2|Layer 2]]
- There are four *Administrative Modes* that can be configured on a switch interface
	- *access*
		- The interface will only serve one *Data* VLAN and one *Voice* VLAN
		- Typically, traffic on access ports is *untagged* because there's only one VLAN, and hosts usually don't know what to do with that traffic
			- Traffic to and from the *Data* VLAN (e.g., a PC) is *untagged*
			- Traffic to and from the *Voice* VLAN (i.e., a VoIP phone) is *tagged*
		- [[DTP]] is disabled on the device
		- If connected to a *trunk* port, it will not form a link
	- *trunk*
		- Statically configured to serve as a *trunk* port, and will never become an access port
		- *DTP* is enabled on the interface **unless** it is disabled with `switchport nonegotiate`
			- DTP frames will not be sent, which can prevent an attack from configuring a trunk and [[VLAN hopping]]
		- If connected to an *access* port, it will not form a link
	- *dynamic auto*
		- Configured with **DTP** to *passively form a trunk* if it is connected to a *dynamic desirable* or *trunk* port
		- However, it will not initiate a transition to a trunk, and will remain an *access* port if connected to a *dynamic auto* or *access* port
	- *dynamic desirable*
		- Configured with **DTP** to *actively forma trunk* if it is connected to a *dynamic desirable*, *dynamic auto*, or *trunk* port
		- If connected to an *access* port, it will remain an *access* port
![[Trunk-2.png]]
Source: Original






# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
