---
aliases:
  - Class A
  - Class B
  - Class C
  - Class D
  - Class E
  - Loopback Address
tags:
  - defs_ccna
dg-publish: true
---
#### IPv4 Address Classes
- There are 5 IPv4 *Address Classes* defined by **RFC 1918**, each allocated to a specific purpose or consumer.
	- NOTE: While occasionally referenced in the **CCNA**, they are not relevant when it comes to [[IP subnet|subnetting]]

| Class              | Purpose                       | First Octet | First Octet Range | Slash Subnet | Dotted Subnet | Private IP Range              | Private IP Subnet Mask |
|:------------------ |:----------------------------- |:----------- |:----------------- |:------------ |:------------- |:----------------------------- |:---------------------- |
| A - "This Network" | RFC Reserved - "This Network" | 0.0.0.0     | -                 | /8           | 255.0.0.0     | 0.0.0.0 - 0.255.255.255       | ---                    |
| A                  | Large networks                | 1-126       | 128               | /8           | 255.0.0.0     | 10.0.0.0 - 10.255.255.255     | /8                     |
| A - Loopback       | RFC Reserved - Loopback       | 127         | -                 | /8           | 255.0.0.0     | 127.0.0.0 - 127.255.255.255   | ---                    |
| B                  | Medium/Large networks         | 128-191     | 64                | /16          | 255.255.0.0   | 172.16.0.0 - 172.31.255.255   | /12                    |
| C                  | Small Networks                | 192-223     | 32                | /24          | 255.255.255.0 | 192.168.0.0 - 192.168.255.255 | /16                    |
| D                  | Multicast addresses           | 224-239     | 16                | ---          | ---           | ---                           | ---                    |
| E                  | Experimental                  | 240-255     | 16                | ---          | ---           | ---                           | ---                    |

# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic
#extop-1-6 #extop-1-7
### Contributors

### Sources
