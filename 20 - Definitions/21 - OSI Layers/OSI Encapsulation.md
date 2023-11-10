---
aliases: null
dg-publish: true
---
Definition: When sender composes a packet, it gets packed up like a Russian doll from [[Layer 7|L7]] to [[Layer 2|L2]] before getting sent over the wire

[OSI Reference Model](https://netcert.tripod.com/ccna/internetworking/osi.html)

| OSI Layers   | TCP/IP Layers | PDU for each layer  | Data Encapsulation (1>7) | Data De-encapsulation (7>1) | 
|:------------ |:------------- |:------------------- |:------------------------ |:--------------------------- |
| Application  | ---           | Data                |                          |                             |
| Presentation | Application   | Data                |                          |                             |
| Session      | ---           | Data                |                          |                             |
| Transport    | Transport     | [[Segment]]         | Packets>Segments         | Segment>Packets             |
| Network      | Internet      | [[Packet]]          | Frames>Packets           | Packets>Frames              |
| Data-Link    | Data-Link     | [[802.3 Frames]] | Bits>Frames              | Frames>Bits                 |
| Physical     | Physical      | [[bits]]            | -                        | -                           |

![[OSI Encapsulation-1.png|600]]


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
