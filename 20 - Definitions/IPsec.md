---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### IPsec
- *Internet Protocol Security* is a secure network protocol suite that authenticates and encrypts packets of data to provide secure encrypted communication between two computers over an Internet Protocol network.
- Framework of open standards that provide secure encrypted communication on an IP network
- IPsec *tunnel* encapsulates the entire original packet
	- Adds a new VPN and IP header
- It is used to create site-to-site [[VPN|VPNs]]
	- Two routers form an *IPsec tunnel* between each other
		- EXAMPLE: A computer sends a packet from Site A to a computer at Site B
			- Router A encrypts the entire packet, and encapsulates with with a VPN header and a new IP header
			- Router A then sends the encrypted packet over the internet to Site B
			- Router B decrypts the data to get the original packet, and forwards it to its destination
			- The computers are unaware of the VPN, and can send unencrypted data between each other securely.

#### IPsec Modes
- *Tunnel mode*
	- The *entire packet* (including original IP headers) is encrypted, *new IP headers* are attached, and the packet is sent
	- Primarily used to connect *two networks* over the internet
- *Transport mode*
	- Only the *payload* of the packet is encrypted, and the *original IP headers* are used
	- Not *suitable for VPNs*, but more compatible with *routing protocols*
	- Typically used to connect *two hosts* over a public network

##### Limitations of IPsec
1. IPsec doesn't support *broadcast* or *multicast* traffic, just *Unicast*
	1. Any protocols that rely on broad- or multicast traffic (e.g., OSPF, EIGRP, etc.) won't work
	2. [[GRE#GRE over IPsec|GRE over IPsec]] resolves this issue
2. Full Mesh IPsec tunnels between networks is difficult to create and maintain
	1. Cisco's [[DMVPN]] can resolve this


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
