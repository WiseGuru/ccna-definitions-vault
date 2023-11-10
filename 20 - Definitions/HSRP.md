---
aliases:
  - Hot Standby Router Protocol
  - Hot Standby Router Protocol (HSRP)
  - Virtual Router Redundancy Protocol (VRRP)
tags:
  - defs_ccna
dg-publish: true
---
#### HSRP
- **Hot Standby Router Protocol** is an [[FHRP]] protocol
- HSRP uses a Virtual IP (VIP) and [[MAC Address|MAC]] address to allow for automated gateway failover
	- The hosts use the VIP as their default gateway address
	- If the active gateway fails, the standby gateway will take over
- Hello messages are sent ever *3 seconds* by default by routes in the *active*, *standby*, or *speak* states
	- Only routers in the *standby* state listen for routers, and takes over if the span between *hello* messages exceeds the *hold time (def. 10 seconds)*
- *VRRP* (Virtual Router Redundancy Protocol) is identical to HSRP, except it uses `vrrp` instead of `standby` for its configuration

![[FHRP#FHRP Virtual MAC Addresses]]
![[FHRP#FHRP Multicast Address Multicast Addresses]]
### HSRP operations
1.  Both [[Router|routers]] have a normal physical [[IPv4|IP address]] and [[MAC Address|MAC]] address on their HSRP interface
	1.  Unique addresses area used on both [[Router|routers]]
2.  They both also have the HSRP VIP and [[MAC Address|MAC]] address configured on the interface
	1.  The same addresses are used on both [[Router|routers]]
3.  When they come online, one is elected to HSRP active router, the other is standby
4.  The active router owns the virtual IP and [[MAC Address|MAC]] address and responds to [[ARP]] requests
5.  All traffic for the VIP goes through the active router
6.  The [[Router|routers]] send hello messages to each other over their HSRP interface
	1.  If the standby router stops receiving hellos from the active, it will transition to be the active router
	2.  It will take ownership of the VIP and [[MAC Address|MAC]] address and respond to ARP requests

### HSRP Router States
1. There are 6 HSRP states
	1. Init
		1. When the link first *comes up*
	2. Learn
		1. The HSRP device is attempting to *learn* the *VIP*
	3. Listen
		1. The device has *learned* the *VIP*
		2. The device is *listening* for *hello* messages from other (*active/standby*) HSRP devices
		3. If a device is not elected to either *active* or *standby*, it remains in the **Listen** state
	4. Speak
		1. The device *sends hello messages* and participates in the *Active router election*
	5. Standby
		1. The device is *actively listening* to *hello* messages from the *Active router*
		2. The default *hold time* is *10 seconds*, roughly 3x the *hello time*
	6. Active
		1. The device *receives data* for and *manages* the *VIP*
		2. Sends *hello messages* ever *3 seconds* (by default)



### Advanced Topics
1. Priority and Preemption
	1. Router priority can be set, with the **higher value** being preferred
		1. Default value is 100
	2. Preemption allows a router to take `Active` when it comes online
		1. Default, preemption is disabled because it can be more stable if there is a fault with the primary router
2. HSRP Version
	1. Version 2 introduced minor improvements
		1. Default version is 1
	2. Both routers must be on the same version
3. Standby Groups
	1. Multiple HSRP "Standby groups" can be configured on interface, allowing for "load balancing" between VLANs or different clients
		1. e.g., R1 is priority in standby 1 10.10.10.1/24, and R2 is priority in standby 2 10.10.20.1/24

### HSRP Configuration
1.  Configure both router interfaces with their IP and "standby IP" (Virtual IP)
	1. Example: VIP is 10.10.10.1
```
R1Config# int g0/1
	Config-if# ip address 10.10.10.2 255.255.255.0
	Config-if# no shut
	Config-if# standby 1 ip 10.10.10.1
	Config-if# standby 1 priority 110
    Config-if# standby 1 preempt
    Config-if# standby version 2
R2Config# int g0/1
	Config-if# ip address 10.10.10.3 255.255.255.0
	Config-if# no shut
	Config-if# standby 1 ip 10.10.10.1
	Config-if# standby 1 priority 90
	Config-if# standby version 2
```
2.  Verification
	1.  `#sho standby`


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

