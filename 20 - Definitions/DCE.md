---
aliases:
  - DTE
tags:
  - defs_ccna
dg-publish: true
---
#### DCE/DTE
- *DCE/DTE* are two sides of a [[Serial]] connection.
	- The **DCE** (*Data Circuit-terminating Equipment, Data Communications Equipment, or Data Carrier Equipment*) transmits the clock signal and controls the clock rate
	- The **DTE** (*Data* **Terminal** *Equipment*) receives the clock signal
- In short:
	- **DCE** Transmits the clock signal and controls the clock rate
	- **DTE** Receives the clock signal

Clock rate only needs to be configured on the DCE
`# sho controllers `
```
R1(config-router)# do sho controllers s0/0/0
Interface Serial0/0/0
Hardware is PowerQUICC MPC860
DCE V.35, clock rate 128000
idb at 0x81081AC4, driver data structure at 0x81084AC0
SCC Registers:
General [GSMR]=0x2:0x00000000, Protocol-specific [PSMR]=0x8
Events [SCCE]=0x0000, Mask [SCCM]=0x0000, Status [SCCS]=0x00
Transmit on Demand [TODR]=0x0, Data Sync [DSR]=0x7E7E
```
The **DCE V.35** indicates that R1 is the DCE in the pair, and controls the clockrate


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

