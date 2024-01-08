---
aliases:
  - Link Aggregation (LAG)
  - LAG
tags:
  - defs_ccna
dg-publish: true
---
#### EtherChannel
- *EtherChannel* is the logical grouping multiple interfaces into a single logical interface (like the reverse of [[Trunk]])
	- However, it is more of a stickler than Trunking/DTP
- There are *three methods* of configuration, and the modes **cannot be mixed**
	- [[PAgP]]
		- #Cisco-Proprietary 
		- *desirable* **actively** attempts to form an EtherChannel
			- Forms EtherChannel with either `desirable` or `auto` neighbors
		- *auto* does not actively attempt to form an EtherChannel
			- Only forms EtherChannel with `desirable` neighbors
	- [[LACP]]
		- Industry standard ([[IEEE]] 802.3ad)
		- *active* **actively** attempts to form an EtherChannel
			- Forms EtherChannel with either `active` or `passive` neighbors
		- *passive* does not actively attempt to form an EtherChannel
			- Only forms Etherchannel with `active` neighbors
	- Static (*LAG*)
		- `on` is the only configuration
			- Both sides must be `on`
				- Anything else results in a failed configuration
		- No Etherchannel negotiation
		- [[WLC]]'s are *only* compatible with *Static/LAG* EtherChannel connections





# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-2-4 #extop-2-7 
### Contributors

### Sources


