---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Wildcard Mask
- A *wildcard mask* (or a host mask) Identifies the *host bits* in an IP address (the opposite of a [[IP subnet|subnet mask]])
	- HOWEVER, Wildcard mask =/= subnet mask
		- A *subnet* has a network address, broadcast address and follows other kinds of rules
		- A *wildcard mask* is literally "Any host with an IP address in this range"
			- e.g., in [[OSPF]], the `network` command looks for any *interfaces IP* that falls in the *wildcard mask* range, and then advertises the *network* associated with that interface.
				- It does **NOT** advertise the inverse-network of the *wildcard mask*
			- Example: `config-router# network 10.0.0.0 0.255.255.255 area 0`
				- It **DOES** grab any IP address that falls between 10.0.0.0 and 10.255.255.255, adds them to Area 0, and advertises their networks
				- It does **NOT** advertise 10.0.0.0/8 on area 0
- Two ways to calculate the wildcard mask
	- *Full*: Flip the subnet bits
		- `11111111.11111111.11111000.00000000`
			- 255.255.248.0
		- `00000000.00000000.00000111.11111111`
			- 0.0.7.255
	- *Shortcut*: Subtract 255 from each octet (and make positive)
		- 255.255.192.0
		- 0.0.63.255
- Wildcard masks are often used in dynamic routing protocols (like [[EIGRP]] and [[OSPF]]) and in [[ACL|ACLs]]



# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
