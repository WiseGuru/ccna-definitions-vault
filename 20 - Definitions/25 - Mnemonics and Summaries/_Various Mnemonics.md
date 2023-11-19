##### NEEDED
1. A list of protocols that perform elections, and whether they prefer higher or lower numbers
	1. e.g., [[HSRP]] prefers higher, OSPF DR/BDR prefers higher, Spanning tree prefers lower, AD/Metric prefers lower, etc.

### Shortcuts for Subnet Masks and Network Classes

**4:12:20:28 = 16** (16 IPs, it's the mid-points)
2^bits

- **n = prefix multiple of 8 (/0, /8, /16, /24, /32)
- Subnet Masks - Octet Divisions
	1. 128 - /n+1
	2. 192 - /n+2
	3. 224 - /n+3
	4. 240 - /n+4
	5. 248 - /n+5
	6. 252 - /n+6
	7. 254 - /n+7
	8. 255 - /n+8
- Subnet Masks - Octet Increments
	1. 128 - /n+1
	2. 64 - /n+2
	3. 32 - /n+3
	4. 16 - /n+4
	5. 8 - /n+5
	6. 4 - /n+6
	7. 2 - /n+7
	8. 1 - /n+8

### Encryption
Symmetric algorithms
1. A 3D Fish in an RC Stream is Symmetric
	1.  A(ES) 3D(ES) (two/blue)fish RC(4)
		1.  [[AES]]
		2.  DES/3DES
		3.  Twofish/Bluefish
		4.  RC4
			1.  RC4 is a stream cypher


![[OSPF#OSPF Mnemonics]]

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


![[802.3 Frames#802.3 Frame Mnemonic]]

![[802.11 Frames#802.11 Frame Format MNEMONIC]]

![[Routing Table#Routing Metrics and AD]]



### Reading Hex

Each character is 4 bits, or a hex bit
1111 = 1/1/1/1 = 8/4/2/1 = 15 = F

0101 = 0/4/0/1 = 5
1011 = 8/0/2/1 = 11 = B
![[IPv6#Unicast/Multicast/Anycast Summary]]
![[IPv6#IPv6 Known Prefixes]]



![[_Ports and Protocols#Important Protocols and Ports to Memorize]]

![[_DNS Song#DNS Song]]

### Cisco Troubleshooting Methodology
1. DGAE-PTSD 
2. Define Problem
3. Gather Information
4. Analyze Information
5. Eliminate Causes
6. Propose Hypothesis
7. Test Hypothesis
8. Solve and Document


### Port Security Modes
**Secure your PRS**-d
Protect
	Like a shield, it just deflects
Restrict
	Deflects and tracks
Shutdown (default)
	Full stop



### FHRP Multicast and MAC Addresses

| IP Address  | Services or Protocols | Description |
| ----------- | --------------------- | ----------- |
| 224.0.0.2   | [[FHRP\|HSRP]]        |             |
| 224.0.0.18  | [[FHRP\|VRRP]]        |             |
| 224.0.0.102 | [[FHRP\|GLBP]]        |             |

- Virtual MAC addresses
	- HSRPv1: **0.c07.acXX** or 00:00:0c:07:ac:XX
	- HSRPv2: **0.c9f.fXXX** or 00:00:0c:9f:fX:XX 
	- VRRP: **0.5e00.1XX** or 00:00:5e:00:01:XX
		- V = 5e00
	- GLBP: **7.b400.XXYY** or 00:07:b4:00:XX:YY 
		- G =/= 5, so G = b400