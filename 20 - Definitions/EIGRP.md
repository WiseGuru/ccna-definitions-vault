---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### EIGRP
- Enhanced Interior Gateway Routing Protocol
- #Cisco-Proprietary  routing protocol, called "advanced" [[Distance Vector Routing Protocols|Distance Vector]] routing protocol
- Much better than [[RIP]], but still a DV protocol
- EIGRP [[Router|routers]] need to have the same Autonomous System (AS) number
	- `Config# router eigrp (AS number)`
		- `Config-router# network (Network address) (Wildcard mask)`
			- [[Wildcard mask]]

### Calculating routes
- **EIGRP Metric** = Bandwidth of *slowest link* + *delay of all links*
- Terminology
	- *Feasible Route* is any route that has a path to the destination
	- *Feasible Distance* is the router's metric value to the route's destination
	- *Advertised Distance* is the neighbor device's *Feasible Distance*
	- **Successor** is the route with the lowest metric to the destination
	- **Feasible Successor** an *guarantied loop-free* alternate route should the *Successor* go down that has a lower *Advertised Distance* than the *Successor's Feasible Distance*
		- The "Lower [[AD]] than Successor's FD" is known as the *Feasibility condition*

**NOTE**: I need a graph here to help illustrate all the EIGRP terms.

#### Unequal-Cost Load-balancing
- This is different from [[ECMP]]
	- By default, EIGRP uses [[ECMP]]
- You can tell EIGRP to load balance between the Successor and the Feasible Successor routes (ONLY the S and FS routes will be load balanced)
	- Change this via *Metric variance Multiplier*
		- `config-router# variance 2`
			- Variance 2 = *Feasible Successor* with an *FD* up to **2x** the *Successor* route's *FD* can be used to load balance


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

