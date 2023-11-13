---
aliases:
  - IPv6 Address
  - IPv6 Addresses
tags:
  - defs_ccna
dg-publish: true
---
#### IPv6
- *IPv6* addresses are **128-bit*** Layer 3 addresses that are split into eight *16-bit* fields called *hextets*
	- Each field is composed of two *hexadecimal* that range from *0-F (0-9, A-F)*
		- 0 - 15 in decimal
		- 0000 - 1111 in Binary
- Addresses can be shortened by *omitting leading 0s* and *summarizing one group* of contiguous *0s as "::"*
	- For example, these addresses are the same
		- 2001:0DB8:0000:0000:0001:0000:0000:0001
		- 2001:DB8:0:0:1:0:0:1
		- 2001:DB8:0:0:1::1

[IPv6 Multicast Address Scopes - IANA](https://www.iana.org/assignments/ipv6-multicast-addresses/ipv6-multicast-addresses.xhtml)
1. IPv6 addresses use **128-bit** addresses split into 8 **16-bit** fields
	1. Each field contains 4 characters that range from **0-9 and A-F**
		1. ![image2](Decimal-Binary-Hexadecimal.png)
	2. The fields are called **hextets, pieces, or quartets** (but are technically hexadectets)
2. Addresses can be shortened by removing leading and contiguous Zeros
	1. Only one set of contiguous Zeros can be shorted to **"::"**
	2.  These addresses are the same:
		1.  2001:0DB8:0000:0001:0000:0000:0000:0001
		2.  2001:DB8:0:1:0:0:0:1
		3.  2001:DB8:0:1::1

### IPv6 Address types
1. *Global Unicast* - **2000::/3**
	1. Global Unicast addresses are assigned to an individual host and can have global reachability (unless blocked)
	2. Internet authorities assign blocks from the overall 2001::/3 range to organizations
		1. A common assignment for a *company* is a */48 block*, e.g. 2001:2:3::/48
	3. Addresses assigned to individual hosts should use a /64 mask
		1. This splits the address in half; 4 hextets for the network ID, 4 hextets for the host address
		2. 64 host bits = 18.44 Quintillion hosts per subnet
	4. This leaves 16 bits for companies to use for subnetting
		1. 16 bits = 16,535 possible subnets
		2. X:X:X \| X \| X:X:X:X
		3.  Company \| Subnet \| Host
2. *Unique Local* - **fd00::/8**
	1. They are equivalent to IPv4's Private address ranges
		1. They are not globally routable
		2. Uses the range *fd00::/8* to assign completely unique addresses to devices
		3. ![[IPv6-unique-local-1.png]] (source: [Unique local address - Wikipedia](https://en.wikipedia.org/wiki/Unique_local_address)) 
			1. The *Global ID* is a 40-bit *Random* hexadecimal string
			2. The *subnet ID* is 16-bits long, and assigned by the administrator
			3. The *interface ID* is 64-bits long and unique to each device
				1. It can either be *stateful* (manually configured) or *stateless* with [[EUI-64]] (automatically generated) with
3. *Link Local* - **FE80::/10**
	1. These addresses are *required* and *automatically created*, and are only valid on the direct link it is connected to.
	2. It is required for [[NDP]] and other 

### Unicast/Multicast/Anycast Summary

1. Unicast
	1. Global Unicast
		1. *2000::/3*
			1. Binary 0010 or 001
	2. Unique Local
		1. *FD00::/8*
			1. Binary 1111 1101
	3. Link Local
		1. *FE80::/10*
			1. Binary 1111 1110
2. Anycast
	1. Packets sent to an "Anycast" address are routed to the nearest device with that "Anycast" address associated with it.
		1. e.g., if you had a network with multiple authentication servers across the globe that were peered and used the same anycast address.
3. Multicast
	1. FF00::/8
		1. First two hextets are always 1111 1111 (FF)
		2. Third hextet are flags (currently all set to 0)
		3. fourth hextet defines the scope
			1. *1*: Interface-local
			2. *2*: Link-local
			3. *5*: Site-local
			4. *8*: Organization-local
			5. *14*: Global scope
		4. The remaining bits are used in the *group ID*, which identifies the recipient
			1. FF02::1 = All nodes on the local network segment
			2. FF02::2 = all routers on the local network segment


## IPv6 Known Prefixes

| Network       | Purpose                                                               |
|---------------|-----------------------------------------------------------------------|
| 2001:db8::/32 | Documentation prefix used for examples                                |
| ::1           | Localhost                                                             |
| Fc00::/7      | Unique Local addresses (ULA) - also known as "Private" IPv6 addresses |
| Fe80::/10     | Link Local addresses, only valid inside a single broadcast domain     |
| 2001::/16     | Global Unique Addresses (GUA) - Routable IPv6 addresses               |
| Ff00::/12     | Multicast Addresses                                                   |

- Well known Multicast Addresses

| Address   | Purpose                  |
|-----------|--------------------------|
| Ff02::1   | All IPv6 devices         |
| Ff02::2   | All IPv6 [[Router|[[Router|[[Router|[[Router|[[Router|routers]]]]]]]]]]         |
| Ff02::5   | All OSPFv3 [[Router|[[Router|[[Router|[[Router|[[Router|routers]]]]]]]]]]       |
| Ff02::a   | All EIGRP (IPv6) [[Router|[[Router|[[Router|[[Router|[[Router|routers]]]]]]]]]] |
| Ff05::1:3 | All DHCP servers         |


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[IPv6 - Wikipedia](https://en.wikipedia.org/wiki/IPv6)
[Unique local address - Wikipedia](https://en.wikipedia.org/wiki/Unique_local_address)