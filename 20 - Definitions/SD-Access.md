---
aliases:
  - Software-defined access
  - software defined access
  - SDA
tags:
  - defs_ccna
dg-publish: true
---
#### SD Access
**Software-Defined Access** provides an additional layer of analysis, controls over access policies, network segmentation, and endpoint monitoring.
	1. It is an all-in-one product that provides another vital layer of security and privacy protection.
	2. The two required components for SD-Access
		1. [[Cisco DNA Center]] for security policy configuration
		2. [[Cisco ISE|Cisco Identity Services Engine (ISE)]] for user authentication.

# SD-Access Functions in [[SDN]] Planes
1. **Management Plane**
	1. Functions that are used to manage devices are part of the Management plane
2. **Control Plane**
	3. [[LISP]] protocol provides the control plane of Cisco SD-Access
3. **Data Plane** (Also known as the *Forwarding* place)
	1. VXLAN protocol provides the data plane of Cisco SD-Access
	2. [[VXLAN]] stands for "Virtual Extensible LAN" and is basically the Overlay
	3. Tasks include forwarding user traffic from one interface to another

4. SD-Access uses an underlay and overlay network
	1. An **underlay** network is the underlying physical network
		1. It provides the underlying physical connections which the overlay network is built on top of
	2. An **overlay** network is a topology used to virtually connect devices
		1. It is built over the physical underlay network
	3. The combination of underlay and overlay forms the SD-Access 'network fabric'

# SD-Access Switch Types
1. Edge Node
	1. At the boundary of the SD-Access Fabric and connects end-devices to the fabric
	2. Responsible for encapsulating traffic into the [[VXLAN|Virtual Extensible LAN (VXLAN)]] and determining the appropriate virtual network
2. Control Plane Node
	1. Holds the location information for all endpoints and serves as a mapping repository
	2. Uses [[LISP]] to provide its mapping service
3. Border Node
	1. Provide connectivity between the SD-Access Fabric and external networks
	2. Responsible for translating VXLAN to its connecting native format


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
