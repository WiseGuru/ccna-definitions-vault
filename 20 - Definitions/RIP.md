---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### RIP
**Routing Information Protocol (RIP)** is an Interior Gateway/Distance Vector Routing Protocol that uses Hop count as the metric.
1. **[[AD]]: 120**
2. **Metric: Hop count**
	1. EXAMPLE: if R1 is trying to get to R4, and it has two paths available (R1>R2>R3>R4 [3 hops] and R1>R5>R4 [2 hops]), it will add the shortest path to its routing table (R1>R5), regardless of bandwidth
		1. Information will get passed along with each hop passing on the route with the number of hops
3. The maximum hop count by default is 15
	1. Paths that are more than 15 hops away are marked as unreachable
4. RIP is not typically used in production because of its scalability issues
	1. Typically only used in small or test environments


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
