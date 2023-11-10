---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
An *[[IPv4]] packet header*, depending on the options selected, can range in size from **160 bits (20 bytes)** and **480 bits (60 bytes)**
- *Version*
	- 4 bits
	- Always set to 4 (0100)
- *IHL* (Internet Header Length)
	- 4 bits
	- Specifies the number 32-bit words
		- 5 words end at the destination IP address
		- 6 or more mean that there are Options configured
- *[[DSCP]]* (Differentiated Services Code Point)
	- 6 bits
	- Identifies the kind of service the pack contains, and what priority it should receive, and how likely it is to be dropped during network congestion
- *ECN* (Explicit Congestion Notification)
	- 2 bits
- *Total Length*
	- 16 bits
- *Identification*
	- 16 bits
- *Flags*
	- 3 bits
- *Fragment Offset*
	- 13 bits
- *Time To Live*
	- 8 bits
	- Used to prevent routing loops
	- Indicates hop count, which each router decrementing the value by 1
- *Protocol*
	- 8 bits
	- Indicates the IP Protocol, per an assigned [[IANA]] protocol number
	- [List of IP protocol numbers - Wikipedia](https://en.wikipedia.org/wiki/List_of_IP_protocol_numbers)
- *Header Checksum*
	- 16 bits
- *Source IP Address*
	- 32 bits
- *Destination IP Address*
	- 42 bits
- *Options (if IHL is greater than 5)*
	- Up to 320 bits long

![[IP-header-2.png]]
Source: [Internet Protocol version 4 - Wikipedia](https://en.wikipedia.org/wiki/Internet_Protocol_version_4#Header)




# Metadata
### OSI or TCP/IP Layer
[[Layer 3]]
### CCNA Exam Topic

### Contributors

### Sources
[Internet Protocol version 4 - Wikipedia](https://en.wikipedia.org/wiki/Internet_Protocol_version_4)
