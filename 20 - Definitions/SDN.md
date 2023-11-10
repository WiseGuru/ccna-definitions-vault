---
aliases:
  - Software Defined Networking
  - Software-Defined Networking
  - Control Plane
  - Infrastructure Plane
  - Application Plane
  - Controller-Based Networking
tags:
  - defs_ccna
dg-publish: true
---
# SDN
Definition: Software-defined networking (SDN) technology is an approach to networking that centralizes the Control plane into an application called a controller
- NOTE: The terms *PLANES* and *LAYERS* may be used *INTERCHANGEABLY*
	- e.g., Boson ExSim uses "*Application Plane*" instead of "*Application Layer*"
- *SDN Planes* focus on functional divisions within the network
	- e.g., a router might perform the functions of both the Data Plane and the Control Plane
- *SDN Layers* focus on the different components, their hierarchy, and their interactions within the SDN Framework
	- e.g., the specific devices that exist at each layer

# Hybrid SDN
- Hybrid SDN allows some or all network devices to retain some control plane intelligence instead of relegating all of it to the SDN Controller
	- There are many reasons you would want a hybrid solution and not just SDN or traditional/legacy
		- Migration
		- Risk management
		- Geographical/functional segmentation
		- Regulatory/compliance
		- etc.etc.

# SDN Planes
1. **Management Plane**
	1. Configures and monitors devices in the Control plane
		1. For example...
			1. via CLI with SSH
			2. via GUI with HTTPS
			3. via [[API]] with SNMP
2. **Control Plane**
	1. Where routing decisions (OSPF, MAC Address Table, [[ARP]], STP, etc.) are made
	2. Considered "overhead" work
		1. OSPF doesn't actually forward frames, but it informs the data plane where to forward packets
3. **Data Plane** (Also known as the *Forwarding plane*)
	1. Where packets are actually forwarded around
	2. Includes functions such as packet encapsulation, [[dot1q|802.1Q]] VLAN tags, NAT, etc.
	3. Uses specialized hardware called [[ASIC|ASICs (Application-Specific Integrated Circuit)]] for switching and logic

**SBI (Southbound Interface)** is a software interface ([[API]]) that allows the *Control Plane* or *Control Layer* to manage the *Data Plane* or *Infrastructure Layer*

# SDN Layers
There are three layers:
1. **Application Layer** -  *SDN Business Applications*
	1. Where SDN Applications reside
		1. These applications address certain needs, such as load balance, network virtualization, and security
	2. [[Northbound API|Northbound APIs]] (NBIs) connect Application and Control layers
		1. typically use [[REST]]
2. **Control Layer** - *SDN Controller (Cisco DNA Center, APIC, etc.)*
	1. Contains the SDN controllers
		2. Controllers communicate with the Application layer to make decisions based on network information
		3. The controllers then communicates with devices in the data plane (the Infrastructure layer) to implement the decisions
	2. [[Southbound API|Southbound APIs]] (SBIs) connect Control and Infrastructure layers
		1. [[OpenFlow]], [[SNMP]], [[REST]], [[NETCONF]], [[RESTCONF]], [[OpFlex]], [[OnePK]], [[OpenFlow]], etc.
3. **Infrastructure Layer** - *Physical networking devices (switches, routers, etc.)*
	1. The devices that perform the functions of the Data Plane




# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
