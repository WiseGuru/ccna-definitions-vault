---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### DHCP
- *Dynamic Host Configuration Protocol* is a client/server protocol that automatically provides a host with its IP address and other related configuration information such as the subnet mask and default gateway.
- DHCP Relay Agent's forward DHCP messages, eliminating the need for a DHCP server on every subnet
- DHCP requests are Broadcast messages

### DHCP Operations
#### **DORA**: DHCP Operations Order
1. **Discover**: DHCP Discover (**Client**, *Broadcast*)
2. **Offer**: DHCP Offer (**Server**, *Unicast/Broadcast*)
3. **Request**: DHCP Request (**Client**, *Broadcast*)
4. **Ack**: DHCP Ack (**Server**, *Unicast/Broadcast*)
#### DHCP Server messages
1. *OFFER*
	1. Initial response to a client request
2. *ACK*
	1. Provisioning of IP address and DHCP information
3. *NAK*
	1. Decline's a user's request for provisioning
		1. Opposite of an ACK
#### DHCP Client Messages
1. *DISCOVER*
	1. Initial packet searching for a DHCP server
2. *REQUEST*
	1. IP address/DHCP information provisioning request
3. *RELEASE*
	1. Release of leased IP address
4. *DECLINE*
	1. Decline offered IP address by a server

### DHCP Commands
- Create a DHCP **pool**
	- `Config# ip dhcp pool <Pool Name>`
- **Lease** shows *detailed* information related to the IP lease itself, like renewal time, client hostname, etc.
	- `# sho dhcp lease`
- **Binding** shows *summary* device-specific information (i.e., MAC address, expiration, etc.)
	- `# sho dhcp binding`

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-4-3 #extop-4-6 
### Contributors

### Sources

