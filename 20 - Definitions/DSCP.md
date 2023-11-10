---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### DSCP
- *Differentiated Services Code Point* marking is the preferred method for [[QoS]] classification and marking because the router can very quickly gather the information from a single byte in the IP header	
	- It replaces the outdated IPv4 TOS field
- It is recommended to mark "scavenger" traffic (traffic from worms, P2P file sharing aps, etc.), with DSCP 8 (CS1)
- *Assured Forwarding (AF)* are markings that indicate a packet's *priority* and when it can be *dropped* during network congestion
	- AF *(priority class)* **(drop probability)**
		- Priority Class
			- A *higher number* indicates the packets are *more time sensitive*
				- e.g., AF3x is multimedia streaming, AF4x is multimedia conferencing, etc.
		- Drop Probability
			- A *higher number* indicates that is is more *likely to be dropped* during network *congestion*

![[DSCP-Classes-1.png]]
Table from Wikipedia

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[DSCP Markings - Cisco](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus1000/sw/4_0/qos/configuration/guide/nexus1000v_qos/qos_6dscp_val.pdf)
[Differentiated services - Wikipedia](https://en.wikipedia.org/wiki/Differentiated_services)
