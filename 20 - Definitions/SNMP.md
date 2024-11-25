---
aliases:
  - Simple Network Management Protocol
tags:
  - defs_ccna
dg-publish: true
---
#### SNMP
-  **Simple Network Management Protocol** is an open standard for network monitoring 
	1. An [[NMS|SNMP Manager]] (the SNMP server) can collect and organize information from an SNMP Agent, which is SNMP software which runs on managed devices such as [[Router|routers]] and [[Switch]] 
		1. The [[NMS|SNMP Manager]] is commonly called an [[NMS|SNMP Server]] or NMS (Network Management System)
		2. The SNMP Agent is often called SNMP device
- You should use [[AES]] encryption for security
![[MIB#MIB]]

### SNMPv3 Configuration
1. Privilege Levels
	1. noauth
		1. *NoAuthNoPriv* - no security features
			1. Backwards compatible with SNMPv2
	2. auth
		1. *AuthNoPriv* - Password, no encryption
			1. Communication is authenticated with a password to ensure authenticity/data integrity
			2. No encryption (hence NoPrv)
	3. priv
		1. *AuthPriv* - Password and Encryption
			1. Authentication and encryption ensure confidentiality, integrity, and authenticity
2. Create a group and set permissions
	1. `config# snmp-server group <group name> v3 <noauth|auth|priv> {access <ACL name> context <VLANs> read <read view> write <write view> notify <notify view>}`
		1. `access`
			1. Limit access to a specific [[ACL]]
		2. `context`
			1. Identify which VLANs are accessible via SNMP
		3. read/write/notify (views of the **MIB** tree)
			1. Read
				1. What the group can read 
			2. Write
				1. What the group can modify
			3. Notify
				1. Which view the group receives TRAP/INFORM messages for
3. Configure a user and assign it to a group
	1. `config# snmp-server user <user name> <name of assigned group> v3 auth <md5|sha> <Auth password> priv <des|3des|aes> <encryption bit level> <Encryption password>`

### SNMP Out-of-Scope
This is likely out of scope, but might come up. More info: [SNMP Version 3 - Server Config - Cisco](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/snmp/configuration/xe-3se/3850/snmp-xe-3se-3850-book/nm-snmp-snmpv3.html#GUID-1CC99199-5205-4099-BE12-06B9A9C202E2)
- Each *SNMP server* must have a unique **engine ID**
	- The *engine ID* is a 10-character [[bits|Hexadecimal]] string that identifies the server
	- By default, the engine ID is built using the *enterprise number* and the default [[MAC Address]] of the device
		- The *enterprise number* is assigned to the device manufacturer by the [[IANA]]
			- Cisco's is *9*
- *SNMP clients* must be configured with a *remote* **engine ID** that matches the server's *engine ID*
	- *Alternatively*, it must identify *IP address* of the SNMP server

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-4-4
### Contributors

### Sources
