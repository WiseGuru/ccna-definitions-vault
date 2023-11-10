---
aliases: Access Control Lists,ACLs,Access Control List
tags: defs_ccna
dg-publish: true
---
#### ACLs
- *Access Control Lists* are used to permit or deny traffic from hosts on a network.
	- They are composed of *ACEs (Access Control Entries)*, each of which defines a particular action
- *ACLs* are then applied on *incoming* or *outgoing* traffic on *interfaces* on a networking device
	- Only *one ACL* can be applied *per direction* on an *interface*
- ACLs use [[Wildcard mask|wildcard masks]] instead of Subnet masks because they are applied on a per-host basis, not on defined networks
- There are two kinds of ACLs
	- Standard ACLs
		- Standard range: 1-99
		- Extended range: 100-199
		- Very simple
			- Just identify an *action (permit/deny)*, and the affected *hosts (source IP address and Wildcard mask)*
	- Extended ACLs
		- Standard range: 1300-1999
		- Extended range: 2000-2699
		- Very granular
			- In addition to the standard ACL, allows the administrator to identify the *destination*, *protocols*, *ports*, and *traffic flags*
- *Named ACLs* allow us to modify and rearrange *ACEs* in an ACL

### ACL Details
1. ACL ranges
	1. Standard: 1-99, 1300-1999
	2. Extended: 100-199, 2000-2699
2. Standard ACLs
	1. Format:
		1. `access-list <ACL number> <permit/deny> <source-IP> <wildcard mask>
3. Extended ACLs
	1. Format
		1. `<permit/deny> <IP protocol> <source address and wildcard> <gt/eq/etc. port number> <destination address and wildcard> <gt/eq/etc. port number> <traffic flag>` 
			1. *Action* **Protocol** *(Source Qualifier Port)* **(Destination Qualifier Port)** *Traffic-flag*
	2. Practice writing out ACLs
		1. Allow all traffic
			1. `config-ext-nacl# permit ip any any`
		2. Prevent 10.0.0.0/16 from sending UDP traffic to 192.168.1.1/32
			1. `config-ext-nacl# deny udp 10.0.0.0 0.0.255.255 192.168.1.1 0.0.0.0`
		3. Prevent 172.16.1.1/32 from pinging hosts in 192.168.0.0/24
			1. `config-ext-nacl# deny icmp host 172.16.1.1 191.168.0.0 0.0.0.255`
		4. Allow traffic from 10.0.0.0/16 to access the server at 2.2.2.2/32 using HTTPS
			1. `config-ext-nacl# permit https 10.0.0.0 0.0.255.255 host 2.2.2.2`
			2. CORRECTION
			3. `config-ext-nacl# permit tcp 10.0.0.0 0.0.255.255 host 2.2.2.2 eq 443`
		5. Prevent all hosts using UDP port numbers from 20000 to 30000 from accessing the server at 3.3.3.3/32
			1. `config-ext-nacl# deny udp rg 20000 30000 any host 3.3.3.3`
			2. CORRECTION
			3. `config-ext-nacl# deny udp any range 20000 30000 host 3.3.3.3`
		6. Allow hosts in 172.16.1.0/24 using a TCP source port greater than 9999 to access all TCP ports on server 4.4.4.4/32 *except* port 23
			1. `config-ext-nacl# permit tcp 172.16.1.0 0.0.0.255 gt 9999 tcp host 4.4.4.4 neq 23`
4. Modifying Named ACLs
	1. Can modify named or numbered ACLs in the same way
	2. Edit the ACL
		1. `config# ip access-list <list type> <list name or number>`
			1. Remove individual entry
				1. `config-std-nacl# no <entry number>`
			2. Insert an entry
				1. `config-std-nacl# <entry number> <permit/deny> <host or network details>`
			3. Resequence entries
				1. `config# ip access-list resequence <list ID> <new number for first entry> <number to increment by>`
					1. e.g., `config# ip access-list resequence 1 5 10` changes the starting entry number to 5, and then increments by 10 (5, 15, 25, etc.)


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

