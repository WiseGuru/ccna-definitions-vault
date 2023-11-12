---
aliases:
  - APs
  - Access Points
  - Wireless Access Point (AP)
  - Wireless Access Points (APs)
  - Wireless APs
  - Lightweight Access Points
  - AP
tags:
  - defs_ccna
dg-publish: true
---
#### Wireless APs
- *Wireless Access Points* provide connectivity between wireless station and between wireless and wired networks
	- Wireless is half-duplex, kind of like a [[Hub]]
		- one device can communicate at a time

##### **APs** operate in 3 different modes
- *Autonomous* (rarely but sometimes called *Local-MAC*)
	- Self-contained system, configured individually
		- RF Parameters, security, QoS, VLANs, etc. are all configured locally
	- Typically connected to a [[Trunk]] port
- [[Lightweight APs]] (also called *Split-MAC*)
	- Form a [[CAPWAP|CAPWAP (Control and Provisioning of Wireless APs)]] tunnel with the [[WLC]]
		- The *Lightweight AP* handles all real-time operations, like wireless traffic, encryption/decryption, etc.
		- *Media Access Control* duties (RF, security, QoS, authentication, etc.) are all offloaded to the *WLC* via the encrypted tunnel
			- All traffic from the AP is tunneled to the *WLC* through the *CAPWAP*
				- *Control* Tunnel: *5246 UDP*
				- *Data* tunnel: *5247 UDP*
	- *Lightweight APs* connect to *Access Ports*, because all traffic is destined for the *WLC*
- *Cloud-based*
	- Between an Autonomous and Lightweight configuration
	- *Data* is routed *locally*, like an autonomous AP
	- *Management* traffic and *Media Access Control Duties* are tunneled to the *cloud controller*
	- [Cisco Meraki](https://meraki.cisco.com/) is a popular option


![[Wireless Service Sets#Service Sets]]


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-1-1 
### Contributors

### Sources
