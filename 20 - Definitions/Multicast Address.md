---
aliases:
  - Multicast
  - Multicast Addresses
tags:
  - defs_ccna
dg-publish: true
---
#### Multicast Addresses
- Multicast addresses are specially designated IP and MAC addresses that are reserved for sending packets to multiple hosts
	- They are not forwarded by routers between subnets


#### Multicast MAC address
- [[802.3 Frames]] are [[Layer 2]], not Layer 3, so Multicast IP addresses must be mapped to MAC addresses
- The reserved range is 01-00-5E-00-00-00 through 01-00-5E-7F-FF-FF
	- The first 24 bits are always 01-00-5E, and the 25th bit is always 0, so the 7th octet can only ever equal 0-7
		- Prefix binary: **00000001.00000000.01011110.0**
	- The remaining 23 bits are derived from the last 23 bits of the IPv4 multicast address
- Example: 224.1.2.3
	- In binary, with the last 23 bits highlighted
		- 11100000.0**0000001.00000010.00000011**
	- Combine the MAC prefix and the IP suffix
		- **00000001.00000000.01011110.0**0000001.00000010.00000011
		- 01-00-5E-01-02-03
- Example: 224.134.36.64
	- In binary, with the last 23 bits highlighted
		- 11100000.1**0000110.00100100.01000000**
	- Combine the MAC prefix and the IP suffix
		- **0000-0001-0000-0000-0101-1110-0**000-0110-0010-0100-0100-0000
		- 01-00-5E-06-24-40



### Multicast Address Table

| IP Address  | Services or Protocols | Description |
| ----------- | --------------------- | ----------- |
| 224.0.0.1   |                       |             |
| 224.0.0.2   | [[FHRP\|HSRP]]        |             |
| 224.0.0.3   |                       |             |
| 224.0.0.4   |                       |             |
| 224.0.0.5   | [[OSPF]]              |             |
| 224.0.0.9   | [[RIP]]               |             |
| 224.0.0.18  | [[FHRP\|VRRP]]        |             |
| 224.0.0.102 | [[FHRP\|GLBP]]        |             |

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
