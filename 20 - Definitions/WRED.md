---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Weighted Random Early Detection
- *Weighted Random Early Detection (WRED)* is a *congestion avoidance* mechanism that addresses packet loss caused by [[Tail Drop]], which occurs when new incoming packets are dropped because a router's queues are too full to accept them
	- Tail Drop causes *Global TCP Synchronization*, where all [[TCP]] sources reduce flow with congestion, then increase flow when congestion is reduced and causes congestion again
- When WRED is implemented, you can configure different tail drop thresholds for each IP precedence or [[DSCP]] value so that lower-priority traffic is more likely to be dropped than higher priority traffic, thereby avoiding Global TCP Synchronization
	- Useful for networks where the majority of traffic uses [[TCP]] because TCP packets that are 


**NOTE:** Typically encountered in higher-level certs, such as the CCNP or CCIE, but Boson likes it, so...



# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
