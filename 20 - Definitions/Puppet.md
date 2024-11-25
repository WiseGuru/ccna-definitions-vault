---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Puppet

##### KEY Summary
- Written in Ruby
- typically agent based
- Puppet Server is the "Puppet Master"
- Clients use "Pull" model on port **TCP 8140**
- Uses [[HTTPS]] to connect to devices
- Uses a proprietary language
- Uses Manifests to define the desired configuration state of devices

##### Broad Summary
- Puppet is a configuration management tool written in Ruby
- Puppet is typically agent-based
	- Specific software must be installed on managed devices
	- Not all Cisco devices support a Puppet agent
- It can be run agentless
	- A proxy agent runs on an external host
	- The proxy agent uses SSH to connect to managed devices and communicate with them
- The Puppet serer is called the "Puppet Master"
- Puppet uses a "Pull" model (client "Pull" configurations from the Puppet Master)
	- Clients uses **TCP 8140** to communicate with the Puppet master
- Uses a proprietary language for its files
- Text files required on the Puppet master:
	- Manifest
		- Defines the desired configuration state of a network device
	- Templates
		- Similar to [[Ansible]] templates
		- Used to generate manifests





# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
