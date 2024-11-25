---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Ansible
##### KEY Summary
- Agentless
- Written in [[Python]]
- Uses a "Push" model
- Uses [[SSH]] to connect to devices
- Uses [[YAML]] for its necessary files
- Ansible Playbooks define actions taken
- Ansible Server is called the "Control Node"

##### Broad Summary
- A configuration management tool owned by Red Hat
	- Written in Python
- Agentless
	- Doesn't require specialized software to be installed on managed devices 
- Uses SSH to connect to devices, make configuration changes, extract information, etc.
- Uses a *Push* model
	- The Ansible server (Control Node) uses SSH to connect to managed devices and *push* configuration changes to them
- Requires several text config files to be created
	- Playbooks
		- Written in [[YAML]]
		- Blueprints of automation tasks
		- Outline the logic and actions of the tasks that Ansible should do
	- Inventory
		- Written in INI, [[YAML]], and other formats
		- List the devices that will be managed by Ansible, including characteristics of each device
	- Templates
		- Written in **Jinja2**
		- Represent a device's config file, with variables instead of values
	- Variables
		- Written in [[YAML]]
		- Lists if variables and their values
		- The values are substituted into the templates to create complete config files

![[Ansible-1.png]]



# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

