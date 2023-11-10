---
aliases:
  - Wireless LAN Controller
tags:
  - defs_ccna
dg-publish: true
---
#### WLC
*Wireless LAN Controller*; Used in combination with the [[CAPWAP|CAPWAP (Control and Provisioning of Wireless Access Points)]] to manage [[Wireless Access Points|Lightweight Access Points]] in large quantities by the network administrator or network operations center. 
- WLC Ports are physical, and WLC Interfaces are logical (virtual)

### WLC Deployment Models
1. Four deployment models 
	1. *Unified WLC deployment*
		1. The default, WLC is a hardware appliance on the network
		2. Each WLC can support about 6000 WLCs
			1. Scale up with more WLCs
	2. *Cloud-based WLC deployment*
		1. (NOT the same as Cloud-based APs)
		2. WLC is a VM, usually in a private cloud or data center
		3. Each WLC VM can support 3000 APs
			1. Scale up with more WLC VMs
	3. *Embedded WLC*
		1. WLC is integrated with a switch
		2. Each embedded WLC can support up to 200 APs
			1. Scalable
	4. *Mobility Express WLC*
		1. WLC is integrated with an AP
		2. Can support up to 100 APs

![[WLC-Ports-Interfaces-1.png]]
Source: [Firewall.cx](https://www.firewall.cx/cisco/cisco-wireless/cisco-wireless-controllers-interfaces-ports-functionality.html)
### WLC Ports
1. *Service Port*
	1. Used for Out-of-Band (OOB) Management and only supports one LAN
		1. Must be connected to an access port on the switch
	2. The *Service Port Interface* is bound to the *Service Port* if it's used
2. *Distribution Port*
	1. Standard network ports that connect to the [[Distribution System (DS)]]
		1. Used for Data Traffic
	2. Usually connect to switch Trunk ports
	3. If there's more than one, they all form a [[EtherChannel|LAG]] by default
3. *Console Port*
	1. For direct management; either RJ45 or USB
4. *Redundancy Port*
	1. Used to physically connect another *WLC* in an [[High Availability|HA Pair]]

### WLC Interfaces
1. *Management Interface*
	1. Used for management traffic, such as SSH, RADIUS, Syslog, HTTPS, etc.
	2. [[CAPWAP]] tunnels are also formed with this interface
2. *Redundancy Management Interface*
	1. Used to manage the "standby" WLC in an [[High Availability|HA Pair]]
3. *Virtual Interface*
	1. Two key roles:
		1. **DHCP Relay** (to relay DHCP requests from wireless clients to the DHCP server)
		2. Redirect address for **web authentication** (e.g., login page)
4. *Service Port Interface*
	1. Bound to the service port and used for Out-of-Band management
5. *Dynamic Interfaces*
	1. Map WLANs to VLANs
		1. e.g., traffic from the "Sales" WLAN is sent to the wired network from the WLC's "Sales" dynamic interface, that's mapped to "VLAN 10 - Sales"
6. *AP Manager Interface*
	1. Used for all [[Layer 3]] communications between the *WLC* and *Lightweight APs* after they have joined the controller

### WLC Management
#### GUI Orientation
1. *Monitor Tab*
	1. Overview of information
	2. Active ports, list of clients and their details, etc.
2. *Controller Tab*
	1. Create and control interfaces
		1. Assign netmask, gateway, DHCP server, [[ACL|ACLs]], etc.
	2. When creating Interfaces, you first *Name* the interface, then assign a *VLAN ID*
3. *WLAN Tab*
	1. Map WLANs to VLANs and configure configure policies for WLANs
		1. When creating a WLAN, you are asked for the *Type*, *Profile Name*, *SSID*, and *ID*, in that order
	2. *WLAN Editor Subtab*
		1. *General Subtab*
			1. WLANs are created disabled by default; *Enable* here
		2. *Security Subtab*
			1. Allows you to configure [[Layer 2|Layer 2]] security settings
				1. Remember: *PSK* = **Personal**, *[[802.1X]]* = **Enterprise**
				2. PSK can be either [[ASCII]] or [[bits|Hexadecimal]]
		3. *QoS Subtab*
			1. Choose the default QoS for that VLAN
				1. *Platinum* = Voice
				2. *Gold* = Video
				3. *Silver* = Best Effort, default
				4. *Bronze* = Background
		4. *Advanced Subtab*
			1. [[FlexConnect]], maximum number of clients, etc.
4. *Wireless Tab*
	1. See and manage all APs connected to the WLC
	2. Also set AP operational mode
		1. local
		2. FlexConnect
		3. Monitor
		4. Rogue Detector
		5. Sniffer
		6. Bridge
		7. SE-Connect
5. *Management Tab*
	1. Change management connection settings like [[SSH]], [[SNMP]], [[HTTP|HTTPS]], etc.
	2. Can also enable wireless clients to manage WLC
6. *Security Tab*
	1. Create and manage [[ACL|ACLs]], [[EAP]], [[RADIUS]]/[[TACACS+]] config, etc.
	2. **CPU ACLs** are used to limit access to the *Central Processing Unit* of the WLC


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[Cisco WLC Interfaces, Ports & Their Functionality. Understand How WLCs Work, Connect to the Network Infrastructure & Wi-Fi SSID/VLAN mappings](https://www.firewall.cx/cisco/cisco-wireless/cisco-wireless-controllers-interfaces-ports-functionality.html)