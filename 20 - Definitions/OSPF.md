---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### OSPF
*Open Shortest Path First (OSPF)* is an <u>Interior Gateway>Link State Routing Protocol</u>. It uses "*Cost*" as the metric, which is automatically derived from interface bandwidth by default
- You can manually configure the costs of links if you want to manipulate the path, but it usually takes the best path anyway
- Uses **Dijkstra's Shortest Path First algorithm** to determine the best path to learned networks
- **Cost** is calculated by **Reference bandwidth / Interface bandwidth**
	- Default reference bandwidth is 100Mbps

### 5 OSPF network types (2 main, 3 odd)
1. 2 Main 
	1. *Broadcast*
		1. Enabled on **Ethernet** and [[FDDI]] links by default
		2. Routers *elect DR/BDR* to reduce overhead
		3. Default **Hello** interval is **10 seconds**, default *dead* time **40 seconds**
	2. *Point-to-Point*
		1. Enabled on [[PPP]] and [[HDLC]] interfaces by default
		2. Simplifies OSPF operation, **no** DR/BDR elections
		3. Default **Hello** interval is **10 seconds**, default *dead* time **40 seconds**
2. 3 Odd (non-broadcast networks, like *Frame Relay*, *X.25*, and *ATM (Asynchronous Transfer Mode*)
	1. *Non-broadcast multi-access (NBMA)*
		1. Emulates a broadcast network (DR/BDR elections)
		2. Every router must be configured with the IP address of its neighbors
		3. Creates **Permanent Virtual Circuits (PVCs)** to be configured between endpoints
		4. Default Hello interval is **30 seconds**
	2. *Point-to-multipoint*
		1. Emulates a point-to-point network
			1. Organizes *PVCs* into a collection of P2p networks
			2. *Hello* packets are replicated and transmitted individually to each neighbor
		2. Default Hello is **30 seconds**
	3. *Point-to-multipoint (non-broadcast)*
		1. `non-broadcast` can be appended to P2m networks to force *unicast* packets instead of *multicast* packets
		2. Default Hello is **30 seconds**

### OSPF Process
1. Discover neighbors
	1. Hello Packets
		1. When OSPF enabled, a router will send out and listen for **Hello** packets to form adjacencies with other OSPF [[Router|routers]]
2. Form Adjacencies
3. Flood Link State Database (LSDB)
	1. First sends **DBD (DataBase Description)**
		1. Adjacent [[Router|routers]] will tell each other their known networks
	2. If a router is missing a route, it will send a **Link State Request (LSR)**
	3. The supplying router will respond with a **Link State Update (LSU)**, which contains one or more **Link State Advertisements (LSA)**
	4. After receiving an **LSU**, the receiver will send an **LSAck (Link State Acknowledgement)** back to the sender
		1. If the sender doesn't receive an **LSAck**, it will resend the **LSU**
4. Compute Shortest Path
5. Install best routes to routing table
6. Respond to network changes

### OSPF Areas and Route Types
- **Areas**
	- Areas are logical groupings of networks, routers, and links
		- They create a hierarchical and more efficient routing domain
		- *Single-area networks do not need to be in Area 0*
	- **Backbone Area (Area 0)**
		- The "Transit area", or the backbone
			- All other areas must connect to Area 0
		- In a multi-area network, it typically does not contain users
	- **Non-backbone Area (areas 1+)**
		- Also called "standard" areas, connect users to Transit area
	- **Stub Area**
		- Doesn't receive external routes (routes from other autonomous systems)
		- Receive the default route and Inter-Area routes
	- **Totally Stubby Area**
		- Doesn't receive External LSAs or Inter-Area routes
		- Only receives the default route injection from the ABR
	- **Not-So-Stubby-Area (NSSA)**
		- Similar to Stub Areas, but they can import external routes as Type-7 LSAs
- **Intra-Area Routes (O)**
	- Routes within the same OSPF area
- **Inter-Area Routes (O IA)**
	- Routes to other OSPF areas, but within the same *Autonomous System (AS)*
- **External Routes**
	- Routes that are injected into OSPF using redistribution from outside of the *AS*
		- The default External Route is *Type 2 External Routes (O E2)*
	- Two types of External routes:
		- **Type 1 External Routes (O E1)**
			- Cost of these routes are the sum of the internal (router to ASBR) and external (ASBR to destination) costs
		- **Type 2 External Routes (O E2)**
			- Just the external cost (ASBR to destination)
- **Loopback Routes**
	- Routes to a Loopback interface on an OSPF-enabled router
	- By default, advertised as host routes with /32 subnet maska

### Router Types
1. **Backbone Routers**
	1. Routers which have all of their OSPF interfaces in Area 0
2. **Area Border Routers (ABRs)**
	1. Routers that have interfaces in multiple areas
	2. Separates LSA flooding zones
	3. Is the primary point for area address summarization
	4. Maintains the LSDB for each area
	5. ABRs do not automatically summarize routes
	6. *Routes to other areas appear as InterArea (IA) routes*
3. **Internal Routers** (also Normal Area Routers)
	1. Routers that have all their interfaces in a normal area (area 1+)
	2. Maintain a full LSDB of routers and links in their area
	3. Learn **Inter-Area (IA)** routes from their ABRs
4. **Autonomous System Boundary Routers (ASBR)**
	1. Redistribute other areas into OSPF
	2. Routes that are redistributed into OSPF appear as **External routes**

### OSPF Packets
1. **Hello** packet **(message type 1)**
	1. When OSPF enabled, a router will send out and listen for Hello packets to form adjacencies with other OSPF [[Router|routers]]
2. **DBD** (DataBase Description) **(message type 2)**
	1. Adjacent [[Router|routers]] will tell each other their known networks
3. **LSR** (Link State Request) **(message type 3)**
	1. If a router is missing information, it will send a Link State Request
4. **LSU** (Link State Update) **(message type 4)**
	1. LSU's are replies to LSR's
	2. Contains one or more LSA's (Link State Advertisements) which should be updated
		1. 4. LSA (Link State Advertisement) is a routing update
	3. When an LSU is sent between [[Router|routers]], it floods the LSA information through the network
5. **LSAck** (Link State Acknowledgement) **(message type 5)**
	1. Sent by receiving [[Router|routers]] after getting the LSAs
	2. Notifies the source OSPF router that the LSA advertised by the LSU has been properly received
	3. The LSU will be re-sent if an LSAck is not received

### OSPF LSA types
| LSA    | Name               | Generated By        | Function                                               | Flooding Map                  |
| ------ | ------------------ | ------------------- | ------------------------------------------------------ | ----------------------------- |
| Type 1 | Router             | Normal Area Routers | Advertising router's interface and status to neighbors | *Intra*-area (area of origin) |
| Type 2 | Network            | DR                  | Advertising DRs direct-connected neighbors             | *Intra*-area (area of origin) |
| Type 3 | Summary            | ABR                 | Advertising ABRs' areas summary                        | Inter-Area (multiple areas)   |
| Type 4 | Summary ASBR       | ABR                 | Advertising the presence of ASBRs                      | Inter-Area (multiple areas)   |
| Type 5 | AS External        | ASBR                | Advertising external routes (to internet)              | Inter-Area (multiple areas)   |
| Type 7 | Not-So-Stubby Area | ASBR                | Advertising external routes to NSSA areas              | Inter-Area (multiple areas)   |


### OSPF Configuration
1. *Process ID*
	1. A Process ID is the ID of the OSPF process to which to the interface belongs, and it is local to the router
		1. Process ID's don't need to match between [[Router|routers]]
	2. It can be used to create two or more overlapping OSPF regions that don't exchange routing information
	3. Typically only 1 process ID is used
	4. Each process ID can be configured
2. *Network*
	1. The Network command means "Look for interfaces with an [[IPv4|IP address]] that falls within a range and enable OSPF on those ports with a specific area"
		1. It uses a [[Wildcard mask]] to identify relevant ports, add them to an area, and then advertise the networks configured on those ports
3. *Passive-Interface*
	1. Passive interfaces do not form adjacencies and do not provide internal information
	2. Should be configured on [[Loopback interface]]
	3. "default" sets all interfaces to be passive by default
4. *IP Route*
	1. Static route injection
5. *Auto-cost Reference-bandwidth*
	1. Change the reference bandwidth when calculating cost; default is 100, should be set to 1000000 or higher
6. *Router ID*
	1. Formed as an [[IPv4|IP address]], typically the highest [[IPv4|IP address]] of the loopback or highest IP on the router if loopback is not configured
	2. Can be set manually, but best practice is to use the loopback
	3. Router ID updates when the OSPF process restarts (read: router reboots)


### OSPF DR (Designated Router) and BDR (Backup Designated Router)
1.  OSPF on multiaccess segments
	1.  On point-to-point links, OSPF router pairs form a FULL adjacency
	2.  On multiaccess segments (such as Ethernet), where there can be multiple routers, it is inefficient for all routers to form a FULL OSPF adjacency with each other
		1.  Rather than sharing full information, just share information with the Designated Router (DR) to fully manage routing
			1.  If the DR goes down, there could be a big problem
		2.  Backup Designated Router (BDR) adds redundancy
2.  *DR*, *BDR*, and *DROTHER*
	1. *DR* (designated router) and *BDR* (backup designated router) are elected based on *priority* and *router ID*
		1.  The router with the highest priority becomes the DR, and the router with the second-highest priority is BDR
			1.  *Default priority* is 1, the highest is 255
			2.  0 says "this router will never be the DR"
		2.  The *highest Router ID* is used in case of a tie
		3. All other routers on the network establish FULL neighbor state with the DR and BDR routers
			1. They will appear as FULL/DR and FULL/BDR
	2. *DRother* routers are **NOT** a *DR* or *BDR*
		1. DRothers only form *full adjacencies* with the *DR/BDR*
			1. On the DR/BDR, the adjacency will look like **FULL/DROTHER**
		2. DRothers remain the *2WAY* state with other *DRother* routers
			1. They will appear as *2WAY/DROTHER*

### Hello packets
1. Sent to the OSPF [[Multicast Address|Multicast]] address of 224.0.0.5 ('all OSPF [[Router|routers]]')
2. Hello Packet contents
	1.  Router ID
		1.  32-bit number that uniquely identifies each OSPF router
	2.  Hello Interval
		1.  How often router sends Hello packets
	3.  Dead interval
		1.  How long a router waits to hear from a neighbor before declaring it out of service
			1.  Default is 4x Hello Interval
	4.  Neighbors
		1.  A list of adjacent OSPF [[Router|routers]] that this router has received a Hello packet from
	5.  Area ID
		1.  The area configured for that interface
	6.  Router priority
		1.  An 8-bit number used to select DR (designated router) and BDR (backup designated router)
	7.  DR and BDR IPv4 address (if known)
	8.  Authentication Flag
		1.  Authentication details if configured
		2.  This is important; stops someone from accidentally or maliciously joining a router to your network
	9.  Stub area flag
		1.  If the area is a stub area
			1.  Stub areas have a default route to their ABR rather than learning routs outside the area

```IOS
! Configure a specific OSPF ID
Config# router ospf (process ID)
!
! Add interfaces to a specific area
Config-router# network (network address) (wildcard mask) area (area number)
!
! Set a passive interface
Config-router# passive-interface ("default"/interface name)
!
! Configure a static route (typically to default gateway)
Config-router# ip route (ip address) (network mask) (IP address of gateway to network)
Config-router# ip route 0.0.0.0 0.0.0.0 (default gateway IP address)
```

### Requirements to form an Adjacency
1. *Area* number must match
2. Interfaces must be on the *same subnet*
3. OSPF process must not be `shutdown`
4. *Unique* OSPF *Router IDs*
5. *Matching Hello* and *Dead* timers
6. *Authentication* settings must match
`7.` *IP [[MTU]]* (Maximum Transmission Unit) settings must *Match*
`8.` OSPF *Network Type* must match

**NOTE**: A mismatch on 7 and 8 will allow routers to become OSPF neighbors, but OSPF will not function properly.


### OSPF Neighbor States
1. Establishing neighbor states
	1.  **Down** - no connection
		1.  R1 sends a multicast Hello packet to 224.0.0.5
			1.  I am 172.16.1.1, and I have no neighbors
			2.  If no response received, link is perceived down after 40 seconds (default)
	2.  **INIT** - Initiate 2-way Communication
	3. **2-Way** - Response hello-packet received
		1.  R2 replies with a unicast Hello packet to 10.0.0.1
			1.  I am 172.16.2.1, and I see 172.16.1.1
				1.  If it had other neighbors, it would include them here
		2.  R1 send a unicast hello packet to 10.0.0.2
			1.  I am 172.16.1.1 and I see 172.16.2.1
		3.  Routers are now in a 2-way communication, but haven't exchanged any routes
		4. *DR* and *BDR* is elected in *2-Way* state
	4.  **ExStart** - Routers negotiate who is going to start the exchange, all traffic in unicast
		1.  R1 sends a DBD (database description) packet
			1.  I will start exchange with my Router ID 172.16.1.1
		2.  R2 replies with a DBD packet
			1.  No, I will start exchange because I have a higher Router ID 172.16.2.1
	5. **Exchange** - Routers exchange DBD information, and respond with *LSAck*
		1.  R2 sends a DBD packet with the its LSDB (link state database) summary
		2.  R1 replies with an LSAck
		3.  R1 sends a DBD packet its LSDB summary
		4.  R2 replies with an LSAck
	6.  **Loading** - Exchange LSRs and LSUs
		1.  R2 sends a LSR (link state request) to R1
			1.  I need full info on 172.16.1.0/24
		2.  R1 sends an LSU
		3.  R1 sends an LSR for 172.16.2.0/24
		4.  R2 replies with an LSU
	7.  **Full** - Neighbors are fully adjacent
		1.  R1 sends an LSAck acknowledging all info
		2.  R2 sends an LSAck acknowledging all info
2. Neighbor State Stages Summary
	1.  **Down**: no active neighbor detected
	2.  **INIT**: *Hello* packet is received from a neighbor
	3.  **2-way**: Neighbor responds, includes both router IDs in *Hello*
	4.  **Exstart**: Primary and Secondary roles determined
	5.  **Exchange**: Database description packets sent
	6.  **Loading**: Exchange of LSRs and LSUs
	7.  **Full**: Neighbors fully adjacent

### Various Commands

- Enable OSPF directly on an interface
	- `config-if# ip ospf <process ID> area <area ID>`
- Modify the OSPF [[AD]] on the local router
	- `config-router# distance <new AD value>`



## OSPF Mnemonics
#### OSPF Network Types
Breathe Fiddy, Elect 10
P2P HD, Tyrant 10
Weird nets 30 secs

Broadcast: Ethernet, FDDI, Elects DR/BDR, Hello 10 seconds
Point-to-Point and HDLC, no elections, Hello 10 seconds
Everything else, Hello 30 seconds
(some of them elect DR, some don't, didn't fit the mnemonic)

#### OSPF Neighbor States
Dinit 2-Wexstart Exchange LoFull

1. Down
2. Init
3. 2-Way
4. ExStart
5. Exchange
6. Loading
7. Full



# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-3-4 
### Contributors

### Sources
