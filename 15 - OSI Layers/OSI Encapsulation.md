---
aliases: null
dg-publish: true
---
#### OSI Encapsulation
- *OSI Encapsulation* is the process of *encapsulating* and *decapsulating* information for transport at the different layers of the [[OSI Model]]
- When a client sends information, it gets packed up into different [[PDU]]s like a Russian doll from [[Layer 7|L7]] to [[Layer 2|L2]] before getting sent over the wire



| OSI Layers   | TCP/IP Layers | PDU for each layer | Data Encapsulation (1>7) | Data De-encapsulation (7>1) |     |
| :----------- | :------------ | :----------------- | :----------------------- | :-------------------------- | --- |
| Application  | ---           | Data               |                          |                             |     |
| Presentation | Application   | Data               |                          |                             |     |
| Session      | ---           | Data               |                          |                             |     |
| Transport    | Transport     | [[Segment]]        | Packets>Segments         | Segment>Packets             |     |
| Network      | Internet      | [[Packet]]         | Frames>Packets           | Packets>Frames              |     |
| Data-Link    | Data-Link     | [[802.3 Frames]]   | Bits>Frames              | Frames>Bits                 |     |
| Physical     | Physical      | [[bits]]           | -                        | -                           |     |

![[OSI Encapsulation-2.png]]
Source: Original


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[OSI Reference Model](https://netcert.tripod.com/ccna/internetworking/osi.html)