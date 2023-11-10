---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### IOS Command Hierarchy
- There are 16 configurable privilege levels (0-15) and 3 authentication levels
	1. *Zero*
		1. Level **0 privilege**
		2. Only access to 5 commands; `enable`, *disable*, `logout`, *help*, `exit`
	3. *User Exec* (Auth. Level 1)
		1. Entered from Zero by hitting "Enter" and authentication
		2. Level **1 privilege**
		3. Very limited read-only access to the router
	4. *Privileged Exec mode* (Auth. Level 2)
		1. Entered with the `> enable` command
		2. Level **15 privilege**
		3. Full access to the router
	5. *Global Configuration* (Auth. Level 3)
		1. Entered with `# Config t`
	6. *X Configuration*
		1. Entered with `Config# interface` or `Config# router ospf` etc.


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources


