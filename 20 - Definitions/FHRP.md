---
aliases:
  - First Hop Redundancy Protocol
  - Gateway Load Balancing Protocol
tags:
  - defs_ccna
dg-publish: true
---
#### FHRP
- First Hop Redundancy Protocols use a Virtual IP (VIP) and [[MAC Address|MAC]] addresses to allow for automated failover
- The network clients use the VIP as their [[Default Gateway]]
	- If a physical gateway fails, another gateway will take over

### FHRP Virtual MAC Addresses
- Virtual MAC addresses
	- HSRPv1: **0.c07.acXX** or 00:00:0c:07:ac:XX
		- 0C7AC
	- HSRPv2: **0.c9f.fXXX** or 00:00:0c:9f:fX:XX 
		- 0C9FF
	- VRRP: **0.5e00.1XX** or 00:00:5e:00:01:XX
		- V = 5e00
		- 05e001 (Oh 5-ee hundred and 1)
	- GLBP: **7.b400.XXYY** or 00:07:b4:00:XX:YY 
		- G =/= 5, so G = b400
		- 7B400

### FHRP [[Multicast Address|Multicast Addresses]]
- *224.0.0.2*
	- HSRPv1
- *224.0.0.9*
	- RIP
- *224.0.0.18*
	- VRRP
- *224.0.0.102*
	- GLBP
	- HSRPv2

### FHRP Protocols
1. **[[HSRP|Hot Standby Router Protocol (HSRP)]]**
	1. #Cisco-Proprietary ; deployed in active/standby pairs
	2. **This is what's covered in the CCNA**
2. [[HSRP|Virtual Router Redundancy Protocol (VRRP)]]
	1. Open standard; deployed in active/standby pairs
	2. Almost identical to [[HSRP]].
		1. One difference is [[HSRP]] uses "standby" and VRRP uses "vrrp"
3. Gateway Load Balancing Protocol (GLBP)
	1. #Cisco-Proprietary ; supports active/active load balancing across multiple routers on the same subnet

1. FHRP-activated routers communicate with each other by sending **multicast** Hello messages
2. When FHRP is configured, the **Virtual IP address** should be configured as the default gateway for hosts
3. The active FHRP router responds to [[ARP]] requests with a **virtual MAC address**
4. [[HSRP]] uses **Active** and **Standby** routers
	1. When [[HSRP]] Standby router switches to active, it will send **[[Gratuitous ARP]] messages**
	2. The [[HSRP]] active router is determined by **Highest priority**, then **highest IP address**
		1. The default priority is 100
	3. HSRPv1
		1. HSRPv1 Mutlicast address is **224.0.0.2**
		2. Virtual MAC address format: **0000.0c07.acXX**
			1. **(XX is [[HSRP]] group number)**
			2. This can be shortened to *0.c07*.acXX
	4. HSRPv2
		1. HSRPv2 Multicast address is **224.0.0.102**
		2. Virtual MAC address format: **0000.0c9f.fXXX**
			1. **(XXX is the [[HSRP]] group number)**
				1. This can be shortened to *0.c9f*.fXXX
	5. [[HSRP]] Commands
		1. Assign virtual IP
			1. `Config-if# standby (group number) ip (IP address)`
		2. Configure priority
			1. `Config-if# standby (group number) priority (Priority number)`
		3. Configure Preemption
			1. `Config-if# standby (group number) preempt`
		4. Configure Version 2
			1. `Config-if# standby version 2`
5. VRRP uses **Master** and **Backup** routers
	1. VRRP Multicast address is **224.0.0.18**
	2. VRRP Virtual MAC address format is **0000.5e00.01XX**
		1. **(XX = VRRP group number)**
		2. This can be shortened to *0.5e00*.1XX
6. [[FHRP|Gateway Load Balancing Protocol]]
	1. Load balances among multiple routers on the same subnet
		1. A single **Active Virtual Gateway (AVG)** is elected
		2. The AVG assigns up to **four** Active Virtual Forwarders **(AVFs)**
	2. [GLBP - Gateway Load Balancing Protocol - Cisco Systems](https://www.cisco.com/en/US/docs/ios/12_2t/12_2t15/feature/guide/ft_glbp.html)
	3. GLBP Multicast address is the same as HSRPv2, **224.0.0.102**
	4. GLBP virtual MAC address format is **0007.b400.XXYY**
		1. This can be shorted to *7.b400*.XXYY
		2. **(XX = GLBP group number, YY = AVF number)**
		3. AVF = Active Virtual Forwarders


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-3-5 
### Contributors

### Sources

