---
aliases: []
tags:
  - defs_ccna
dg-publish: true
---
#### Routing Table
- The *Routing Table* identifies [[IP]] routes to networks
	- The **most specific route** (e.g., the route with the *longest prefix*) is the route that is chosen for any given traffic
- Routes can be [[Static route]] by the administrator, or *dynamically added* through routing protocols like [[RIP]], [[EIGRP]], or [[OSPF]]
- How Routes are selected, from creation to packet forwarding
	- Dynamic Routing Protocols choose routes to advertise based on *Metric*
		- The *Metric* process is different for each protocol
			- **OSPF** uses *cost*, and calculates *reference bandwidth/interface bandwidth*
			- **RIP** does a simple hop count, from *0-15*
			- **EIGRP** boils down to *slowest link* + *delay of all links combined*
	- The router collects all routes that are advertised to it and decides which ones will appear on the table based on *Administrative Distance*
		- [[AD|Administrative Distance]] is basically how much the router trusts the route, from *0-255*, with lower being more trustworthy
			- All *Unique routes* from different sources are added to the table
			- If there are multiple *identical routes*, then the one with the *lowest [[AD]]* is added
				- Example: Two Three routes are solicited from different protocols
					- Routes:
						- An EIGRP route (*AD 90*) to 172.31.0.0/*16*, on *Fa02*
						- An OSPF route (*AD 110*) to 172.31.0.0/*16*, on *Fa03*
						- An OSPF route (*AD 110*) to 172.30.16.0/*20*, on *Fa01*
						- An EIGRP route (*AD 90*) to 172.30.0.0/*16*, on *Fa04*
					- The *EIGRP* route on *Fa02* will be selected for the table instead of the *OSPF* route on *FA03*
					- The *OSPF* route on *Fa01* AND the *EIGRP* route on *Fa04* will be added to the table, because they are unique
				- **Floating Static Routes** are *identical routes* that are manually configured with a *slightly higher AD* than what's been added to the table, so if the existing route fails, the *floating static route* will fail-over
		- *[[AD]] does not impact route selection*, just whether it is added to the table
	- The router receives a packet and sends the packet on the route with the *most specific (longest prefix)* matching network
		- Example: A router receives a packet for 172.31.20.232, and there are four routes to pick from
			- Routes:
				- A static route (*AD 1*) to 172.16.0.0/*8*, on *Fa01*
				- An EIGRP route (*AD 90*) to 172.31.0.0/*16*, on *Fa02*
				- An OSPF route (*AD 110*) to 172.31.16.0/*20*, on *Fa03*
				- An Internal BGP route (*AD 170*) to 172.31.20.0/*24*, on *Fa04*
			- The router will send the packet out of interface *Fa04* because that route has the longest prefix.
	- If there is no matching network on the table, the packet be forwarded out of the *Gateway of last resort*
		- This the catch-all network, `0.0.0.0 0.0.0.0`, and the router that sits between the LAN and the WAN

![[Static route#IPv6 Routes]]

#### Configure a [[Static Route]]
`config# ip route <destination> <subnet mask> <next hop> <opt: AD>`
`config# ipv6 route <destination network and mask> <opt: exit interface> <opt: next hop address> <opt: AD>  `


### Routing Metrics and AD
| Protocol               | Type            | AD  | Metric                                           |
| ---------------------- | --------------- | --- | ------------------------------------------------ |
| Connected Interface    | -               | 0   | -                                                |
| Static Route           | -               | 1   | -                                                |
| External BGP           | Path Vector     | 20  |                                                  |
| Internal EIGRP         | Distance Vector | 90  | Bandwidth of *slowest link* and total *Delay*        |
| IGRP (Deprecated)      |                 | 100 |                                                  |
| OSPF                   | Link State      | 110 | *(Ref. Band/Interf. Ban)* |
| IS-IS                  | Link State      | 115 | Cost of all links / config                       |
| RIP                    | Distance Vector | 120 | *Hop count* (All speeds equal)                     |
| External EIGRP         | Distance Vector | 170 | Bandwidth and Delay                              |
| Internal BGP           | Path Vector     | 200 |                                                  |
| Unknown/unusable route |                 | 255 | Route not installed                              |

## Practice Tables






# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-3-1 #extop-3-2 #extop-3-3 
### Contributors

### Sources
