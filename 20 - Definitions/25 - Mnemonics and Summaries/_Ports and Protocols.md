
### Important Protocols and Ports to Memorize

#### [[IANA]] Port ranges
**Well-known**: 0 - 1023
**Registered**: 1024 - 49151
**Ephemeral/private/dynamic**: 49152 - 65535


##### Rhymes/Mnemonics:
**FTP**
- In FTP, Data comes first (FTPD 20 T)
- FTPD 20-ought T
- FTPC 21 T
**DHCP**
- in DHCP, Server comes before client, unlike SNMP
- 
#### TCP
| Protocol       | Port   |
| -------------- | ------ |
| FTP Data       | 20  T  |
| FTP Control    | 21   T |
| SSH            | 22  T  |
| Ansible (SSH)  | 22 T   |
| Telnet         | 23 T   |
| SMTP           | 25 T   |
| DNS            | 53 T/U |
| HTTP           | 80  T  |
| POP3           | 110  T |
| HTTPS          | 443  T |
| Puppet (HTTPS) | 8140 T |
| [[Chef]] (HTTPS)   | 10002 T (also maybe 443 T)     |

#### UDP
| Protocol              | Port   |
| --------------------- | ------ |
| DNS                   | 53 T/U |
| DHCP Server           | 67 U   |
| DHCP Client           | 68 U   |
| TFTP                  | 69 U   |
| NTP                   | 123 U  |
| SNMP Agent            | 161 U  |
| SNMP Manager          | 162 U  |
| Syslog                | 514 U  |
| CAPWAP Control tunnel | 5246 U |
| CAPWAP Data Tunnel    | 5247 U |

