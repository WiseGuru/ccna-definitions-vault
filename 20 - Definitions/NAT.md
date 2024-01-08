---
aliases:
  - Static NAT
  - Dynamic NAT
  - PAT
  - Dynamic NAT with Overload
tags:
  - defs_ccna
dg-publish: true
---
#### NAT
*Network Address Translation (NAT)* is a way to map multiple private IP addresses inside a local network to a public [[IPv4|IP address]] before transferring the information onto the internet.

1. *Static NAT*
	1. Permanent one-to-one mapping between a public and private [[IPv4|IP address]]
	2. Usually used for servers
2. *Dynamic NAT*
	1. Uses a pool of available public IP addresses which are given out as-needed, first-come-first-served
	2. Requests are dropped once the pool runs out
3. *PAT*
	1. Port Address Translation, also called Dynamic NAT with Overload, is a type of dynamic NAT that bands several local IP addresses to a singular public one using [[Layer 4|Layer 4]] ports
	2. It can use one or more public IP addresses
		1. The first public [[IPv4|IP address]] is assigned like normal in Dynamic NAT
		2. The last public [[IPv4|IP address]] is translated using port numbers


#### Configuring NAT
1.  Configure NAT translate from one interface to another
	1.  `Config# int (external interface)`
		1.  `Config-if# ip nat outside`
	2.  `Config# int (internal interface)`
		1.  `Config-if# ip nat inside`
	3.  You can have multiple inside and outside interfaces
2.  [[NAT|Static NAT]] configuration
	1.  `Config# ip nat inside source (static/dynamic) (internal IP) (outbound, external IP)`
3.  [[NAT|Dynamic NAT]] configuration
	1.  Configure the pool of global addresses
		1.  `Config# ip nat pool (pool name) (IP range start) (IP range end) netmask (subnet mask)`
	2.  Create an access list which references the internal IP addresses we want to translate
		1. ` Config# access-list (list number, e.g. 1) permit (internal IP network address) (wildcard mask)`
	3.  Associate the ACL with the NAT pool to complete the config
		1.  `Config# ip nat inside source list (list number) pool (pool name) (OPT:overload)`
		2. `overload` enables [[NAT|PAT]]
4.  [[NAT|PAT]] with DHCP
	1.  Set the outside interface to DHCP
5.  Clearing NAT tables
	1.  `# clear ip nat translation`
		1.  Can also target specific inside and outside configs
	2.  `# clear ip nat translation *`
		1.  Clears all dynamic NAT translations
6.  Verification
	1.  `# sho ip nat translation`
		1.  The NAT table will expire entries fairly quickly
		1.  **KEY DEFINITION**
			1.  *INSIDE* = internal device address
			2.  *OUTSIDE* = external device address
			3.  *LOCAL* = local perspective (local router, local network admin, etc.)
			4.  *GLOBAL* = external perspective (internet, external network admin, etc.)
		2.  Inside local address
			1.  The [[IPv4|IP address]] actually configured on the inside host's OS
		3.  Inside global address
			1.  The NAT'd address of the inside host as it will be reached by the outside network
		4.  Outside local address
			1.  The [[IPv4|IP address]] of the outside host as it appears to the inside network
		5.  Outside global address
			1.  The [[IPv4|IP address]] of the outside host assigned by the host's owner
	2.  `# sho ip nat statistics`
	3.  `# debug ip nat`
		1. Translated addresses appear as `(address 1)->(address 2)`, and the inside local/global addresses will flip depending the direction of the packets
			1.  Outbound
				1. Translated *source* will be listed first as `s=(inside local)->(inside global)`
			2.  Return Traffic
				1. Translated *destination* will appear as `d=(inside global)->(inside local)`
		2. ![[renditionDownload.jpg]]
			1. Source: [Cisco Learning Network](https://learningnetwork.cisco.com/s/question/0D53i00000Kt0gWCAR/nat-debug)
			2. The router is translating outbound traffic to the external host at 170.1.1.1 from the *inside local* address of 10.1.1.1 to the *inside global* address of 200.1.1.2
			3. The router is translating inbound traffic from the external host at 170.1.1.1 from the *inside global* address of 200.1.1.2 to the *inside local* address of 10.1.1.1
# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-4-1 
### Contributors

### Sources
