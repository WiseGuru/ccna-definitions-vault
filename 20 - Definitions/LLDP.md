---
aliases:
  - Link Layer Discovery Protocol
tags:
  - defs_ccna
dg-publish: true
---
#### LLDP
- *Link Layer Discovery Protocol* is a [[Layer 2|Layer 2]] neighbor discovery protocol that allows devices to advertise device information to their directly connected peers/neighbors.
- It is an open standard which provides similar information to [[CDP]]
- Sends *advertisements* every *30 seconds* when enabled on an interface
	- `config# lldp timer <seconds>`
- The LLDP *Reinitialization timer* is set to *2 seconds* by default
- LLDP *Hold Time* (how long the switch will wait before discarding the information) by default is *120 seconds*
	- `config# lldp holdtime <seconds>`
- You can see the LLDP advertisement and hold time with `show lldp`
	- ![[LLDP-1.png]]




# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-2-3
### Contributors

### Sources
