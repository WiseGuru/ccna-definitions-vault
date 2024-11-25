---
aliases:
  - subnetting
  - subnet
  - subnet mask
tags:
  - defs_ccna
dg-publish: true
---
#### IP Subnet
*IP Subnets* are boundaries between logical networks in the IP space.
- 
- [[IPv4]] Subnet masks can be written in *dotted-decimal* (e.g., 255.255.0.0), or in [[CIDR]]/slash notation (e.g., /16).
- The first address in a subnet range is reserved for the Network Address, and the last address is reserved for the [[Broadcast Address|Broadcast]] Address
	- Therefore, the number of host address is the size of the subnet range minus 2
- A *subnet mask* is the opposite of a [[Wildcard mask]]. 

## Shortcuts for Subnet Masks and Network Classes
- **n = prefix multiple of 8 (/0, /8, /16, /24, /32)
- Subnet Masks - Octet Divisions
	1. 128 - /n+1
	2. 192 - /n+2
	3. 224 - /n+3
	4. 240 - /n+4
	5. 248 - /n+5
	6. 252 - /n+6
	7. 254 - /n+7
	8. 255 - /n+8
- Subnet Masks - Octet Increments
	1. 128 - /n+1
	2. 64 - /n+2
	3. 32 - /n+3
	4. 16 - /n+4
	5. 8 - /n+5
	6. 4 - /n+6
	7. 2 - /n+7
	8. 1 - /n+8
- Network Class Divisions
	- **FORGET CLASS DIVISIONS; JUST REMEMBER HOW TO DO IT**
	1. [[IPv4 Address Classes|Class A]]: 128 (0.0-127.255)
		1. *[[IPv4 Address Classes|Class A]] Private: (10.0-10.255) /8*
	2. [[IPv4 Address Classes|Class B]]: 64 (128.0-191.255)
		1. *[[IPv4 Address Classes|Class B]] Private: (172.16.0-172.31.255) /12*
	3. [[IPv4 Address Classes|Class C]]: 32 (192.0-223.255)
		1. *[[IPv4 Address Classes|Class C]] Private: (192.168.0-192.168.255) /16*
	4. [[IPv4 Address Classes|Class D]]: 16 (224.0-239.255)
	5. [[IPv4 Address Classes|Class E]]: 16 (240.0-255.255)
- Network classes
	1. Valid Network [[IPv4 Address Classes|Class C]] range is 192.0.0.0 to 223.255.255.0/24
	2. Valid Network [[IPv4 Address Classes|Class B]] range is 128.0.0.0 to 191.255.0.0/16
		1. Private range is 172.16.0.0 172.31.0.0 /12
	3. [[IPv4 Address Classes|Class A]] valid network addresses range from 1.0.0.0 to 126.0.0.0/8
		1. 0.0.0.0/8 is reserved by RFC to mean "this network"
	4. [[IPv4 Address Classes|Class D]] addresses range from 224.0.0.0 to 239.255.255.255

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-1-6
### Contributors

### Sources
