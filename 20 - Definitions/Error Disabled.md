---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### errdisabled 
- Ports can enter an error-disabled (errdisable) state if it breaks policy and is configured to do so.

| Command                                                      | Description                                                                             |
| ------------------------------------------------------------ | --------------------------------------------------------------------------------------- |
| `SW1:# show errdisable recovery`                             | Show *errdisable* configuration                                                         |
| `SW1:# show port-security <interface ID>`                    | Review port-security status and logs on an interface                                    |
| `SW1:# show errdisable detect`                               | Shows all supported *Errdisable* reasons                                                |
| `SW1:config# errdisable recovery cause <violation>`          | Enables automatic recovery for specific violation causes (psecure-violation, all, etc.) |
| `SW1:config# errdisable recovery interval <time in seconds>` | configures the amount of time *errdisabled* ports will take to recover                  |


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

