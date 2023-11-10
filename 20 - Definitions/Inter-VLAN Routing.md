---
aliases:
  - Router with Separate Interfaces
  - Layer 3 Switch
tags:
  - defs_ccna
dg-publish: true
---
- Router with Separate Interfaces
	- Routers configure each interface to a different [[VLAN]]
	- Less likely to suffer congested lines, but more likely to run out of interfaces
- [[ROAS|Router on a Stick]]
	- Traffic for multiple VLANs are trunked on a single interface
	- Each VLAN is assigned to a virtual sub-interface
	- More likely to suffer congested lines
	- The [[dot1q]] tag in a [[802.3 Frames|Frame]] specifies the sub-interface
- Layer 3 Switch
	- Takes over some Layer 3 functions of a router, such as local VLAN/Subnet switching
	- Intra-campus traffic routed on switch backplane, reducing hops to external router
	- Router may still be needed for WAN connected and other services
- Configuration
	- Router: Create the sub interface on the [[Trunk|Trunking]] interface
		- `config# int <interface>.<VLAN ID>`
			- That is, `config# int g0/1.10`
	- Router: Configure the sub interface to operate on a specific VLAN
		- `config-subif# encap dot1q <vlan ID>`
		- If the sub-interface belongs to the *native* VLAN, don't forget to add `native` at the end
	- Router: No shut the *main interface* to enable all sub-interfaces
		- `config-if# no shut`
	- Switch: Configure interface to function as a trunk port, with the allowed VLANs
		- `config-if# switchport mode trunk`
		- `config-if# swithcport trunk allowed vlan <VLAN IDs separated by commas>`

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

