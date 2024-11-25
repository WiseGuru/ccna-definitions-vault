---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### YAML
1. Definition: *YAML Ain't Markup Language* (Originally, *Yet Another Markup Language*) is a human-readable format where whitespace is significant, and is used by [[Ansible]]
	1. Often used in [[Python]], Perl, and [[Ansible]]
		1. Ansible Playbook uses YAML
	2. Designed to be easily read by humans
		1. White space (indentation) is important
			1. anything at a common indentation level is considered related at the same level
2. YAML Formatting
	1. starts with `---`
	2. `key: value representation`
	3. `-` indicates a list
###### YAML Sample
```YAML
---
NETWORKING:
	domain_name: cisco.com
	domain_name_servers: [171.70.168.183]
	networks:
	- gateway: 192.168.50.1
	  pool: [192.168.50.100 to 192.168.50.2504
	  segments: [management, provision]
	  subnet: 192.168.50.0/24
	  vlan_id: 105
```
# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[Cisco Sample setup_data.yaml File](https://www.cisco.com/c/en/us/td/docs/wireless/asr_5000/21-6-x_6-2-bx/Ultra-M-Solution-Guide-with-CVIM/6-2-bx-UMSG-with-CVIM/UMSG-with-CVIM_appendix_01001.pdf)


> [!info]- Created (dynamic):: `$= dv.current().file.ctime`
> Date created (stamp): 2023-11-06
> Updated:: `$= dv.current().file.mtime`


