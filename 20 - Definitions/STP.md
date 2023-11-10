---
aliases:
  - Spanning Tree Protocol
tags:
  - defs_ccna
dg-publish: true
---
#### STP
- The *Spanning Tree Protocol (STP)* is a network protocol that builds a loop-free logical topology for Ethernet networks.
STP DOES NOT DO LOAD BALANCING

1. Switches send **Bridge Protocol Data Units (BPDUs)** out all ports when they come online to detect potential loops
	1. The BPDU contains the switch's **Bridge ID** that uniquely identifies it on the LAN
		2. The Bridge ID is comprised of the switch's unique **MAC Address** and an administrator defined **Bridge Priority Value**
			1. e.g., 32768.1111.2222.3333
		3. The default Bridge Priority Value is **32768**, and changes in increments of **4096**
		4. In the case of a Bridge Priority Tie, the switch with the lowest **MAC Address** will be selected as the Root Bridge
	2. Manually configure a switch to be the Root Bridge for a VLAN
		1. `Config# spanning-tree vlan (VLAN ID) root primary`
		2. `root secondary` sets the *Bridge Priority* to 28672
	3. There are three ports in 802.1D STP
		1. Root Port
			1. Port with the best path cost
			2. Non-root bridges can only have one root port
		2. Designated Port
			4. Opposite-ports to Root Ports on neighboring switches
			5. All ports on the Root Bridge are Designated Ports
		3. Blocked ports
			1. Blocking ports sit further down the line, opposite to Designated ports
			2. STP only blocks one port in the link
	4. Determining Port Status
		1. **Determine the Root Bridge:**
			1. This is done based on the lowest _Bridge ID_ (Bridge Priority + MAC).
		2. **All ports on the Root Bridge are Designated Ports (DP):**
			1. Every active port on the Root Bridge will forward frames, hence they're all DPs.
		3. **Determine the Root Port (RP) on all non-Root Bridge switches:**
			1. Identify the port with the lowest path cost to the Root Bridge. This cost accounts for the entire path, not just the directly connected link. 
			2. In case of a tie (multiple paths with the same cost):
				1. Choose the path to the neighboring switch with the lowest Bridge ID. 
				2. If there's still a tie, select the path to the neighboring port with the lowest port priority.
				3. Lastly, if there's still a tie, select the path to the neighboring port with the lowest port number.
		4. **Determine the Designated Port (DP) for each network segment:**
			1. The switch connected to the segment that has the lowest path cost to the Root Bridge assigns its port as the DP for that segment.
		5. **Determine Non-Designated Ports (NDP):** 
			1. Any port on a non-root switch that isn't a Root Port or Designated Port becomes an NDP. 
			2. Ports on non-Root switches that connect to the Root Bridge, but aren't the chosen Root Port, are NDPs. 
			3. For segments between non-Root switches, the switch with the higher path cost to the Root Bridge (or loses tie-breakers) will have its connecting port as the NDP.
		6. **Tie-breakers for Designated Ports on equal cost links:** 
			1. Lowest Bridge ID.
			2. Lowest Port Priority.
			3. Lowest Port number.
2. Optional Features
	1. UplinkFast
		1. Enables a blocked port when the Root Port link is failed
	2. BackboneFast
		1. Provides fast convergence 
	3. **PortFast** allows ports to come online in a *Forwarding State* by default
		1. Set all ports to Portfast by default
		2. `Config# spanning-tree portfast default`
	4. **BPDU Guard** prevents broadcast storms on Portfast ports by shutting down immediately upon receipt of a BPDU 
		1. `Config-if# spanning-tree portfast`
		2. `Config-if# spanning-tree bpduguard enable`
	5. **Root Guard** prevents an unintended switch from becoming the root bridge
		1. `Config-if# spanning-tree guard root`
3.  [[IEEE]] Open Standards:
	1.  **802.1D** Spanning Tree Protocol (STP)
		1.  Uses one Spanning Tree for all [[VLAN|VLANs]] in the LAN
		2. Two port states
			1. *Blocking*
				1. When a port first comes online, it will be in a blocking state as STP searches for a loop
			2. *Forwarding*
				1. If no loop is detected, it twill transition to Forwarding
	2.  **802.1w** [[Rapid STP]] (RSTP)
		1. Significantly improved convergence time
		2. All switches originate BPDUs
		3. Uses one Spanning Tree for all the VLANs
		4. Three port states
			1. Discarding (Blocking)
			2. Learning (Learns MAC address, does not forward information)
			3. Forwarding (Forwarding)
		5. Four port roles
			1. Root Port
				1. Port with the best path cost
				2. Non-root bridges can only have one root port
			2. Designated Port
				4. The Root-port pair used as a forwarding port for every LAN segment
			3. Alternate Port
				1. Backup of the switch's own Root Port
				2. Discarding port that receives a superior BPDU from another switch
			4. Backup Port
				1. Backup of the switch's Designated port
				2. Discarding port that receives a superior BPDU from the same switch
	3.  **802.1s** Multiple Spanning Tree Protocol (MSTP)
		1.  Enables grouping and mapping [[VLAN|VLANs]] into different spanning tree instances for load balancing
4.  Cisco Versions
	1.  Cisco released enhancements to the open standards
		1.  **Per VLAN Spanning Tree Plus (PVST+)**
			1.  Cisco enhancement to *802.1D*
			2.  Uses a separate spanning tree for every VLAN
			3.  *PVST+* is the *default* on Cisco [[Switch|Switches]]
		2.  **Rapid Per VLAN Spanning Tree Plus (RPVST+)**
			1.  Cisco enhancement to *802.1w RSTP*
			2.  Significantly improved convergence time over PVST+
			3.  Uses a separate spanning tree instance for every VLAN
	2.  The Cisco versions do not support grouping multiple [[VLAN|VLANs]] into the same instance
5. Misc
	1. *MAC Flapping* or *MAC Address Flapping* is when the same MAC address is active on two ports within a network.
		1. Normally when a device disconnects from the network, it's address is immediately purged from the CAM table
		2. This is almost always an indication of a loop in the network, but could also be an attacker on the network
			1. Attacks include CAM table poisoning, [[Layer 2 Attack Types|MAC spoofing]], etc.

### STP Cost
(table from [PacketLife.net](https://packetlife.net/blog/2008/sep/5/spanning-tree-port-costs/))
![[STP-Costs-1.png]]

### Mapping Ports
1.  The easy way to figure out which ports are Root, Designated, and Non-Designated (Alternate Root)
2.  Determine the Root Bridge first (lowest *Bridge ID* (Bridge Priority + MAC))
3.  All ports on the Root bridge are Designated Ports
4.  Determine the Root Ports on the other [[Switch|switches]]
	1. Lowest cost to Root Bridge, not always the connected link
	2. If multiple links, then it's the port whose neighboring Designated port is the lowest
5. Determine Connected Non-designated ports
	1. Ports connected to the Root Bridge that are not Root Ports are Non-Designated
6. For the remaining links, determine the lowest-cost path to the Root Bridge
	1. The originating port is the Non-designated port, and the receiving port the Designated port
	2. Tie-breakers for equal cost links:
		1. Lowest Bridge ID
		2. Lowest Port Priority
		3. Lowest Port number

1. **Determine the Root Bridge:**
	1. This is done based on the lowest _Bridge ID_ (Bridge Priority + MAC).
2. **All ports on the Root Bridge are Designated Ports (DP):**
	1. Every active port on the Root Bridge will forward frames, hence they're all DPs.
3. **Determine the Root Port (RP) on all non-Root Bridge switches:**
	1. Identify the port with the lowest path cost to the Root Bridge. This cost accounts for the entire path, not just the directly connected link. 
	2. In case of a tie (multiple paths with the same cost):
		1. Choose the path to the neighboring switch with the lowest Bridge ID. 
		2. If there's still a tie, select the path to the neighboring port with the lowest port priority.
		3. Lastly, if there's still a tie, select the path to the neighboring port with the lowest port number.
4. **Determine the Designated Port (DP) for each network segment:**
	1. The switch connected to the segment that has the lowest path cost to the Root Bridge assigns its port as the DP for that segment.
5. **Determine Non-Designated Ports (NDP):** 
	1. Any port on a non-root switch that isn't a Root Port or Designated Port becomes an NDP. 
	2. Ports on non-Root switches that connect to the Root Bridge, but aren't the chosen Root Port, are NDPs. 
	3. For segments between non-Root switches, the switch with the higher path cost to the Root Bridge (or loses tie-breakers) will have its connecting port as the NDP.
6. **Tie-breakers for Designated Ports on equal cost links:** 
	1. Lowest Bridge ID.
	2. Lowest Port Priority.
	3. Lowest Port number.

### Practice networks

#### Problem
![[STP-Example-1.png]]
#### Solution
![[STP-Example-Solution.png]]


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[Spanning tree port costs - PacketLife.net](https://packetlife.net/blog/2008/sep/5/spanning-tree-port-costs/)