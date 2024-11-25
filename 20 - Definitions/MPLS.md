---
aliases:
  - MPLS VPN
tags:
  - defs_ccna
dg-publish: true
---
#### MPLS
- *Multiprotocol Label Switching* is a routing technique in telecommunications networks that directs data from one node to the next based on **labels** rather than network addresses.
	- *Labels* identify established *paths between endpoints*
		- *Network addresses* identify *endpoints*
	- *Label switching* allows service providers to create [[VPN|VPNs]] for clients over their shared infrastructure
- **Core Infrastructure**
	- *CE router* (Customer Edge router)
		- Router at the edge of the *customer*'s network that connects to the *PE*
		- Do not use MPLS, and the MPLS network is *transparent (invisible)* to the customer network
	- *PE router* (Provider Edge router)
		- Router at the edge of the *provider*'s network that connects the *CE*
		- When *PE* routers receive frames *CE* router, they add a label between the *[[Layer 2]]* and *[[Layer 3]]* headers
	- *P router* (Provider core router)
		- The *internal network infrastructure* of the *provider*'s network
		- *P* routers make forwarding decisions based on the *label* on the frames





# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
