---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Intermediate System - Intermediate System
Definition: Link State Routing protocol; Intermediate System - Intermediate System
1. IS-IS (Intermediate System -- Intermediate System) uses "Cost" as the metric, but it is not automatically derived from interface bandwidth
	1. You can manually configure the cost of links if you want to manipulate the path
2. If you do not manually set the link costs, then the path with the lowest hop count will be used
	1. Similar automatic results to [[RIP]] metric, but can be modified by the administrator
3. IS-IS links need to be manually configured or it will use hop count to determine the best path
	1. It is typically only used in Service Provider networks or large organizations with their own MPLS network who choose it because of its scalability
4. Default [[AD]] ([[AD|Administrative Distance]]): 115

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
