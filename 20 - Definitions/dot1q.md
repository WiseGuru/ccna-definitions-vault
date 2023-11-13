---
aliases:
  - 802.1Q
tags:
  - defs_ccna
dg-publish: true
---
#### dot1Q
- [[IEEE]] **802.1Q** encapsulation tags [[Layer 2|Layer 2]] [[802.3 Frames|frames]] for trunking
- Dot1Q trunks are configured on the links between [[Switch|switches]] where we need to carry traffic for multiple VLANS
	1.  The default on older devices is [[ISL]], a Cisco Proprietary trunking protocol, now obsolete
	2.  When the [[Switch]] forwards traffic to another [[Switch]], it tags the layer 2 Dot1Q header with the correct VLAN
	3.  The receiving [[Switch]] will only forward the traffic out ports that are in that VLAN
	4.  The [[Switch]] removes the Dot1Q tag from the Ethernet frame when it sends it to the end host
1. *PCP* (Priority Code Point) field can be used to identify high/low priority traffic

### 802.1Q tag
- **4 bytes**
- First **two bytes** is the *TPID (Tag Protocol ID)*, which is **0x8100**
	- This indicates that the frame is *tagged for VLANs*
- Last **two bytes** is the *TCI (Tag control information)*, and contains the *PCP*, *DEI*, and *VID*
	- *Priority Code Point (PCP)*
		- 3-bit field identifying Class of Service ([[CoS]])
	- *Drop eligible indicator (DEI)*
		- 1-bit field that indicates if a frame can be dropped when the network is congested
	- *VLAN Identifier (VID)*
		- 12-bit field identifying the frame's [[VLAN]], allowing up to *4,094 VLANs*
			- 12-bits = 4096 total possible values *minus* top and bottom (*0* and *4095*)

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-2-2 
### Contributors

### Sources


