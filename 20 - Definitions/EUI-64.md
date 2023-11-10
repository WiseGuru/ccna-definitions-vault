---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---

#### EUI-64
- **EUI-64 (Extended Unique Identifier)** is a method to automatically configure [[IPv6]] host addresses
	1. A [[MAC Address|MAC]] address is a /48 address compared to the /64 host portion of the IPv6 address
	2. FF:FE is injected in the middle of the /48 MAC address to bring it up to 64 bits
	3. Additionally, the 7th bit in the MAC address is inverted
		4. For example, a [[MAC Address|MAC]] address starts with FC
			1. FC in binary is 111111<u>0</u>0
			2. Flip the 7th bit to 111111<u>1</u>0
			3. It is now FE
		5. Example 1
			1. *ca*01.2f24.0000
			2. 2001:DB8:0:1: *C8*01:2F**FF:FE**24:0
		6. Example 2
			1. *ca*01.2f24.0038
			2. 2001:DB8:: *C8*01:2F**FF:FE**24:38
- There are two ways to configure it on an interface
	- Manually specifying the network:
		- `config-if# ipv6 address <network address> eui-64`
	- Using [[NDP]] to automatically configure the address
		- `config-if# ipv6 address autoconfig`


2.  EUI-64 Addresses
	1.  A Cisco router can generate full IPv6 addresses for itself when given the interface and /64 network to use
		2. The host portion of the address is derived from the interface's [[MAC Address|MAC]] address, which is guaranteed to be globally unique
		3. A [[MAC Address|MAC]] address is a /48 address compared to the /64 host portion of the IPv6 address
		4. FF:FE is injected in the middle of the /48 MAC address to bring it up to 64 bits
		5. Also, the 7th bit is inverted
			1. For example, a [[MAC Address|MAC]] address starts with FC
				1. FC in binary is 111111<u>0</u>0
				2. Flip the 7th bit to 111111<u>1</u>0
				3. It is now FE
	2. The router will borrow the [[MAC Address|MAC]] address from the first ethernet port for non-Ethernet interfaces such as Serial ports
	3. It is best not to use EUI-64 on router interfaces
		1. It is better to use a memorable address such as 2001:db8:0:1::1
		2. EUI-64 is much more useful for use with hosts
3. Configure EUI-64
	5. Config# int f0/0
		1. `Config-if# ipv6 address 2001:db8:0:1::/64 eui-64`
	6. Config# int f2/0
		1. `Config-if# ipv6 address autoconfig`
4.  EUI-64 Address Verification
	1.  \# sh int f0/0
		1.  ! Hardware is DEC21140, address is ca01.2f24.0000
	2.  \# sh int f2/0
		1.  ! Hardware is DEC21140, Address is ca01.2f24.0038
	3.  \# sh ipv6 interface brief
		1.  ! FastEthernet 0/0 (up/up)
		2.  ! 2001:DB8:0:1:C801:2FFF:FE24:0
		3.  ! FastEthernet 2/0 (up/up)
		4.  ! 2001:DB8::C801:2FFF:FE24:38

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources


