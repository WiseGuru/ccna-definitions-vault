---
aliases:
  - Address Resolution Protocol
  - ARP Cache
tags:
  - defs_ccna
dg-publish: true
---
#### ARP
- *Address Resolution Protocol (ARP)* maps [[IPv4|IP address]] to [[MAC Address|MAC]] addresses at [[Layer 2]]
- ARP requests and replies are [[802.3 Frames|Frames]] that include the target [[IPv4|IP address]], the sender's [[MAC Address]], and either the [[Broadcast Address|Broadcast]] MAC address or the target's [[MAC Address|MAC]] Address
	- If the [[Switch]] doesn't have the know the target [[MAC Address|MAC]] address, it broadcasts out the request to all ports
	- Hosts that receive frames with mismatched target [[MAC Address|MAC]] addresses will drop the frame
	- The source and destination IP addresses never change
	- The [[MAC Address|MAC]] address changes at each hop
	- At each hop, the ARP cache is updated to expedite future requests.
- Mapped addresses are saved to a host's **ARP Cache** and the Switch's [[MAC Address|MAC]] Address Table, which allows the host to send unicast [[Unicast Address|Unicast]] packets directly to the destination
- When sending an ARP request outside of the [[IP subnet|subnet]], the host will first contact its [[Default Gateway]]
	- Sender wants to send ARP request to destination outside of its [[IP subnet|subnet]]
	- It first sends an ARP request to its Default Gateway's [[IPv4|IP address]]
		- the DG replies with its own [[MAC Address|MAC]] address
	- The sender then sends a request with the Target's IP, but uses the DG's [[MAC Address|MAC]] address
	- The DG then forwards the ARP request to the appropriate [[IP subnet|subnet]]
		- The target replies with its [[MAC Address|MAC]] address
	- The DG then forwards to reply to the sender




# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-5-7
### Contributors

### Sources

