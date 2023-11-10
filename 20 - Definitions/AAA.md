---
aliases:
  - MFA
  - Multi-Factor Authentication
  - 2FA
tags:
  - defs_ccna
dg-publish: true
---
#### AAA
- Authentication, Authorization, Accounting
	- **Authentication**
		- Verifying a user or device's *identity* via one or more factors
			- *Knowledge*
				- Password, pre-set PIN, mother's maiden name
			- *Possession*
				- [[RSA]] SecurID token, soft token (e.g. Authy), SMS code, etc.
			- *Inherent*
				- Biometrics (fingerprint, face, voice, iris, etc.)
			- *Location*
				- Physical location acce
		- *Multi-Factor Authentication* (MFA, 2FA, etc.) uses two or more factors to verify a user's identity
			- A password and PIN are only *one factor* of authentication
			- A PIN and an SMS code are *two factors*, and therefore suffice for *MFA*
	- **Authorization**
		- *Provisioning of access* assigned *to the user or device*
			- A guest may successfully authenticate, but they are not authorized to access the file server
		- In networks, this can mean assigning [[VLAN|VLANs]] to devices after it connects to the network
	- **Accounting**
		- [[Logging]] the activity for later review or immediate action


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

