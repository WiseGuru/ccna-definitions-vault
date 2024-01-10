---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Syslog
- *Syslog* is a standard [[Logging]] format. 
- Each entry follows this format: `seq no:timestamp: %facility-severity-MNEMONIC:description`
	- *seq no*: Sequence number
		- ONLY stamped if `config# service sequence-numbers` is enabled
	- *timestamp*: Date and time of event
		- `config# service timestamps log <datetime/uptime>`
	- *facility*: Service or Hardware generating the message
	- *severity*: 0-7, EACEWNID
	- *MNEMONIC*: Short description (Title)
	- *description*: Detailed information on event

![[Syslog-SeverityLevels.png]]


### Syslog Severity
*EACEWNID* Starts at **0**
0. Emergency
1. Alert
2. Critical
3. Error
4. Warning
5. Notify/Notification
6. Informational
7. Debugging


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-4-5 
### Contributors

### Sources
