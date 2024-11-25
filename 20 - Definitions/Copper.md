---
aliases:
  - UTP
  - 10BASE-T
  - 100BASE-TX
  - 1000BASE-T
  - RJ45
  - STP
  - straight through
  - crossover
tags:
  - defs_ccna
dg-publish: true
---
#### Copper Twisted-Pair Cables
- Copper wires are the most common network cabling media in homes and offices
- Twisted-Pair cables are either *Shielded (STP)* or *Unshielded (UTP)*
	- *Copper Shielded Twisted Pair (STP)* cables reduce noise and [[Interference]] by insulating the twisted-pair wires.
	- *Copper Unshielded Twisted Pair (UTP)* are cheaper than STP cables, but are more prone to interference
- *STP* and *UTP* cables can support [[PoE]], reducing wiring overhead for [hard-to-reach places.](https://www.youtube.com/watch?v=atJDnYICIvw)
- Copper cables are frequently terminated with a *Registered Jack 45 (RJ45)*^[[Registered jack - Wikipedia](https://en.wikipedia.org/wiki/Registered_jack)] plug
	- These cables can by wired as *straight through* or *crossover*^[[Straight Through Cables vs Crossover Cables](https://www.guru99.com/difference-between-straight-through-crossover-cables.html)]
		- *Straight through* cables
			- Wired the same on both sides
				- i.e., orange-stripe on 1, solid orange on 2, etc.
			- Used to connect devices of different types together
				- e.g., a router and a computer
		- *Crossover* cables
			- Each side of the cable is wired a little differently
				- i.e., the orange and green twisted pairs flip on each side of the cable
			- Used to connected two devices of the *same* type
				- e.g. two computers, two switches, etc.
	- [[MDI-MDIX|Auto-MDIX]] is configured on most modern networking equipment to allow network administrators to use either *straight through* or *crossover* cables without issue


### Maybe Not CCNA Relevant
- There are 4 wire pairs in a *UTP* cable, with each cable in a colored pair either *solid* or *striped*
	- Orange
	- Blue
	- Green
	- Brown
- In *traditional [[Ethernet]]* (10BASE-T and 100BASE-TX, or *Ethernet* and *Fast Ethernet*), only TWO out of the four available pairs are used for data transfer
- In 1000BASE-T (Gigabit) and above, all 4 pairs are used


# Metadata
### OSI or TCP/IP Layer
[[Layer 1]]
### CCNA Exam Topic
#extops-1-3 
### Contributors

### Sources
[What's correct order of wires & pins for CAT5/CAT6/CAT7/CAT8/network patch/Ethernet cable (How to make RJ45 cable etc.) (T568A vs T568B which one to use?) (What is 8P8C?) < Blog-D without Nonsense](https://dannyda.com/2021/11/05/whats-correct-order-of-wires-pins-for-cat5-cat6-cat7-cat8-network-patch-ethernet-cable-how-to-make-rj45-cable-etc/)
