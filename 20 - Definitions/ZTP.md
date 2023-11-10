---
aliases:
  - Zero Touch Provisioning
  - Zero Touch Configuration
  - Zero-Touch Configuration
tags:
  - defs_ccna
dg-publish: true
---
#### ZTP
- *Zero Touch Provisioning (ZTP)* is an automatic configuration protocol that allows [[Lightweight APs]] to receive configurations from a [[WLC]]
- There are several ways for a *Lightweight AP* to receive configuration instructions
	- [[DHCP]] - `option 43` gives the [[IPv4|IP address]] of the WLC
		- Most commonly used method
	- [[DNS]] - `cisco-capwap-control` resolves the IP of the WLC
	- Local [[IP subnet|subnet]] broadcast
- *Zero-Touch Configuration* can can also be used with [[Cisco DNA Center]] to configure other network devices
- *ZTP* is also a cloud-based service hosted by Cisco that allows [[vBond Orchestrator]]s and [[vEdge Router]]s to connect to each other

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
