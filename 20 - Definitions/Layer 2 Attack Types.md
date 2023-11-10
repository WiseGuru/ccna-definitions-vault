---
aliases:
  - VLAN Hopping
  - MAC Flooding
  - MAC Spoofing
  - DHCP Spoofing
  - ARP Poisoning
  - CAM Table Overflow
  - ARP Spoofing
tags:
  - defs_ccna
dg-publish: true
---
#### [[VLAN]] Hopping
- *Double-tagging [[dot1q|802.1Q]]* frames on a *trunk* link to move between VLANs
- Mitigate by *disabling DTP*, change the *native VLAN* to an unused VLAN, and configure all user-facing interfaces as *access ports*

#### [[MAC Address|MAC]] Flooding (or [[CAM Table]] Overflow)
- An attacker floods a switch with frames to *overwhelm* a switch's MAC table
	- The switch stops making forwarding decisions, and all traffic is *flooded*
	- The attacker is able to *view all traffic* being sent *on the switch*
- Mitigate by configuring [[Port Security]] with a *maximum* number of allowed MACs on *Access* ports

#### MAC Spoofing
- An attacker *spoofs* a *valid MAC* address to impersonate another device and bypass *port security*
- Possibly mitigate *port security* with *sticky MACs*
	- Also possibly [[DAI]] to validate IP and MAC address associations
- **[[AAA]]** and **[[802.1X]] with device certificates** are the *actual solution*, but are probably **not on the CCNA**

#### [[DHCP]] Spoofing
- An Attacker inserts a rogue *DHCP Server* to intercept and *redirect* traffic
- Mitigate with [[DHCP Snooping]] to restrict *DHCP traffic* to *trusted ports*

#### [[ARP]] Poisoning (or ARP Spoofing)
- An attacker sends *Gratuitous ARP* messages to a host, associating the attacker's *MAC* address with another host's valid *IP* address
- Mitigate with [[DAI]] to intercept and validate *ARP* messages



# Metadata
### OSI or TCP/IP Layer
[[Layer 2]]

### CCNA Exam Topic

### Contributors

### Sources
