---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
### UDP
*User [[Segment|Datagram]] Protocol* is a best-effort [[Layer 4|Layer 4]] protocol
1. UDP segments are called **datagrams**
2. *Not* connection-oriented
	1. No connection is established before data is transmitted by the host
3. *Does Not* provide reliable communication
	1. Acknowledgements are not sent, and lost segments are not retransmitted
	2. Segments are sent *best-effort*
4. *Does Not* provide sequencing
	1. If sequences arrive out of order, there is no mechanism to reconstruct them in order
5. *Does not* have flow control
	1. No mechanism like [[TCP]]'s *Window Size* to control flow of traffic
6. Best used for streaming video/audio content
#### UDP Header
![[UDP-header-1.png]]
Source: [Wikipedia](https://en.wikipedia.org/wiki/User_Datagram_Protocol#UDP_datagram_structure)
#### Common protocols and ports:
Port 69,  [[TFTP]]
Port 161, [[SNMP]]
Port 53, [[DNS]]

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-1-5
### Contributors

### Sources
[User Datagram Protocol - Wikipedia](https://en.wikipedia.org/wiki/User_Datagram_Protocol)