---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Port-Security
- **Port-security** is a switchport command that enables moderates port access through MAC address restrictions and policies
- To configure port security, you must first enable it on the interface with `switchport port-security`
	- Additionally, the switchport must be manually configured as either an *access* or a *trunk* port
- There are *three* violation modes
	- **Protect**
		- Interface remains up
		- Traffic from violating devices is dropped
		- Violation counter is not incremented
		- No log entry is generated
	- **Restrict**
		- Interface remains up
		- Unauthorized frames are discarded
		- Violation counter is incremented each time an unauthorized frame is received
		- A log entry is generated
	- **Shutdown**
		- Interface enters an [[Error Disabled]] state if more MAC addresses connect to an interface than are allowed
		- A log message is generated
		- Violation counter is set to 1

**NOTE**: Much of the following was taken from [Roberto Téllez GitHub Cisco-IOS-Command-CheatSheets.](https://github.com/r7perezyera/Cisco-IOS-Command-CheatSheets)
### Configuring Dynamic Port Security
Command|Description
---|---
``S1(config)#interface [int-id]``|
``S1(config-if)#switchport mode access``|Set interface mode to *access*.
``S1(config-if)#switchport port-security``|Enable port security on the interface
``S1(config-if)#switchport port-security violation [violation-mode]``|set violation mode (``protect``, ``restrict``, ``shutdown``)

>**Best practice:** It is a best security and general practice to "hard-type" the `switchport mode access` command. This also applies to Trunk ports (`switchport mode trunk`).

### Configuring Sticky Port Security
Command|Description
---|---
``S1(config)#interface [int-id]``|
``S1(config-if)#switchport mode access``|Set interface mode to *access*.
``S1(config-if)#switchport port-security``|Enable port security on the interface
``S1(config-if)#switchport port-security maximum [max-addresses]``|Set maximum number of secure MAC addresses allowed on port
``S1(config-if)#switchport port-security mac-address sticky``|Enable sticky learning
``S1(config-if)#switchport port-security violation [violation-mode]``|set violation mode (``protect``, ``restrict``, ``shutdown``)

### Verifying Port Security & secure MAC addresses
Now that we have configured Port Security, the following commands will be handy to verify and troubleshoot.

Command|Description
---|---
``S1#show port-security interface [int-id]``|displays interface's Port Security configuration. If violations occured, they can be checked here.
``S1#show port-security address``|displays secure MAC addresses configured on **all switch interfaces**
``S1#show interface [int-id] status``|displays port status. Useful to verify if an interface is in ``err-disabled`` status.

### Bringing an [[Error Disabled]] interface back up

After a violation, a port in **Shutdown violation mode** changes its status to *[[error disabled]]*, and is effectively **shut down**. To resume operation (sending and receiving traffic), we must bring it back up. Here's how:

* Access the interface configuration mode with ``S1(config)#interface [int-id]``.
* Shut the interface down using ``S1(config-if)#shutdown``.
* Bring the interface back up using ``S1(config-if)#no shutdown``.


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[GitHub - r7perezyera/Cisco-IOS-Command-CheatSheets: A collection of Cisco switch and router IOS commands that everyone can use as reference/guide.](https://github.com/r7perezyera/Cisco-IOS-Command-CheatSheets)