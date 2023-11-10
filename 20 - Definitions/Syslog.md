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





# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
