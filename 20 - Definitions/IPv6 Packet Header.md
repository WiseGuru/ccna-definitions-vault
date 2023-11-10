---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### IPv6 Header
**320 bits** in total (**40 bytes**)
- Version: 4 bits
	- Always 6 (0110)
- Traffic class: 6+2 bits
	- QoS Markings
- Flow Label: 20 bits
	- Used to identify specific traffic flow
- Payload length: 16 bits
	- Length of the encapsulated [[Layer 4]] segment
- Next Header: 8 bits
	- Indicates the encapsulated [[Layer 4]] protocol
- Hop Limit: 8 bits
	- Functions like the IPv4 [[TTL]] field
- Source Address: 128 bits
- Destination address: 128 bits
![[IPv6-Packet-header-1.png]]
Source: [IPv6 packet - Wikipedia](https://en.wikipedia.org/wiki/IPv6_packet#Fixed_header)




# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[IPv6 packet - Wikipedia](https://en.wikipedia.org/wiki/IPv6_packet)