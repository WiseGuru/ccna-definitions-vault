---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### VTP
- *VLAN Trunking Protocol (VTP)* allows you to add, edit, or delete [[VLAN|VLANs]] on [[Switch|switches]] configured as VTP servers, and have other [[Switch|switches]] configured as VTP clients synchronize their VLAN database with them
- VTP Clients and Servers will synchronize their VLAN Databases to the VTP Server with the highest database revision number

### VTP Modes
1. VTP Server
	1. Can add, edit, or delete [[VLAN|VLANs]]
	2. A VTP server will synchronize its VLAN databvase from another VTP Server with a higher revision number
2. VTP Client
	1. Cannot add, edit, or delete [[VLAN|VLANs]]
	2. a VTP client will synchronize its VLAN database from the VTP Server with the highest revision number
3. VTP Transparent
	1. Does not participate in the VTP domain
	2. Does not advertise or learn VTP information but will pass it on
	3. Can add, edit, or delete [[VLAN|VLANs]] in its own local VLAN database
#### VTP Mode Chart

| Function                         | VTP Server | VTP Client | VTP Transparent |
| -------------------------------- | ---------- | ---------- | --------------- |
| Create/Modify/Delete VLANS       | X          |            | X               |
| Synchronizes VTP Information     | X          | X          |                 | 
| Originates VTP Advertisements    | X          | X          |                 |
| Forwards VTP Advertisements      | X          | X          | X               |
| Stores VLAN Information in NVRAM | X          |            | X               |



### VTP Configuration

1. VTP Configuration
	1.  Join the VTP domain
		1.  `SW1config# vtp domain (domain name)`
	2.  Set mode to Server, Client, or Transparent
		1.  `SW1config# vtp mode (server/client/transparent)`
	3.  Adding VLAN to database if server or transparent (cannot add if VTP client)
		1.  `Config# vlan (VLAN number)`
			1.  `Config-vlan# name (VLAN name)`
	4.  Verify VTP Status
		1.  `#show vtp status`

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-2-2
### Contributors

### Sources
