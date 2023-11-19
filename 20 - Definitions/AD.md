---
aliases:
  - Administrative Distance
tags:
  - defs_ccna
dg-publish: true
---
#### AD
- *Administrative Distance* is a measure of how trusted a routing protocol is compared to other protocols
	- However, *AD* does *NOT* determine which route a packet will take, only *whether* it is added to the *routing table* in the event of *duplicate routes*
- A *lower* AD means that a route is *more* trusted
- A **floating [[static route]]** is a *[[static route]]* with a *higher AD* than the preferred route
	- It is configured as a *backup* should the preferred route fail


| Route source        | Default AD |
| ------------------- | ---------- |
| Connected interface | 0          |
| [[Static route]]    | 1          |
| [[BGP]]             | 20         |
| [[EIGRP]]           | 90         |
| [[OSPF]]            | 110        |
| [[IS-IS]]           | 115        |
| [[RIP]]             | 120        |


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-3-2 
### Contributors

### Sources


