---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### DTP
- *Dynamic Trunking Protocol* is a #Cisco-Proprietary  tool to allow *switchports* to automatically negotiate a [[Trunk]]
	- While Cisco is very proud of it, and it *will probably come up on the CCNA*, it is a **security risk** (see [[Layer 2 Attack Types|VLAN Hopping]]) and should be disabled using the `switchport nonegotiate` command


### DTP Commands
1. Switchport/VLAN Configuration
	1. `Config-if# switchport ?`
		1. *mode*: Set trunking mode of the interface
			2. `Config-if# switchport mode ?`
				1. *access*: Set trunking mode to ACCESS unconditionally
				2. *dynamic*: Dynamically negotiate access or trunk mode
					1. `Config-if# switchprot mode dynamic ?`
						1. *auto*: Set negotiation parameter to 'auto' (i.e. passive)
						2. *desirable*: Set negotiation parameter to 'desirable' (i.e. active)
				3. *trunk*: Set trunking mode to TRUNK unconditionally
		2. *access*: Set access mode characteristics (e.g., client access)
			1. `Config-if# switchport access vlan (vlan ID)`
		3. *trunk*: Set trunk mode characteristics (e.g., which [[VLAN|VLANs]] are allowed)
			1. `Config-if# switchport trunk allowed vlan (VLAN IDs separated by commas)`
		4. *nonegotiate*: disable DTP on the interface
			1. `Config-if# switchport nonegotiate`


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-2-2 
### Contributors

### Sources


