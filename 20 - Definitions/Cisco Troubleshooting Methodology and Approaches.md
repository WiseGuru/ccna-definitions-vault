---
aliases: 
tags:
  - defs_ccna
dg-publish: true
---
#### Methodology vs. Approaches/styles
- A *methodology* describes a prescribed path taken to *systematically solve problems*
- An *approach or technique* is a way to *gather information* by addressing *heuristically targeting* specific network elements first

# Troubleshooting Methodologies
## Cisco Official Troubleshooting Methodology
The *Official Cisco Troubleshooting Methodology*^[[Troubleshooting Overview Cisco Systems](https://www.cisco.com/en/US/docs/internetworking/troubleshooting/guide/tr1901.html)] is an 8-step process that loops back and forth around itself.

>**Always** (*always, at any step, for any reason*) **DOCUMENT** *any* and *all changes* that have been made.

1. **Define the problem** in terms of *symptoms* and *potential causes*
2. **Gather facts**
	3. Ask affected users, and collect information from [[NMS]], [[PCAP]]s, output from [[Diagnostic Commands]], etc.
3. **Analyze information** and **eliminate potential causes**
	1. The *elimination of potential causes* is critical to create an efficient action plan
4. **Create an action plan** which changes *only one variable* at a time
	1. This plan should target potential causes from *most likely* to *least likely*
5. **Implement Action Plan**
	1. *Document all changes made*
6. **Gather results of each change**
7. **Analyze** the results to **determine if issue is resolved**
	1. If resolved, *document changes* and process is complete.
8. **If unresolved, return to step 4**

In an effort to make this more *visually comprehensible*, I've drafted this flow-chart.

![[Cisco Troubleshooting Methodology.jpg]]
Source: Original

## Flackbox Troubleshooting Methodology
*Neil Anderson* with [FlackBox](https://www.flackbox.com/the-cisco-troubleshooting-methodology) proposes a similar but different strategy. I've decided to include it here because it may be easier for you to memorize, and is basically the same steps, but expanded.

>  It also makes a handy acronym, DGAE-PTSD


1. **D**efine the problem
2. **G**ather information
3. **A**nalyze information
4. **E**liminate potential causes
5. **P**ropose hypothesis
6. **T**est Hypothesis
7. **S**olve Problem and **D**ocument Solution

![[Cisco Troubleshooting Methodology-1.png]]
Source: [FlackBox](https://www.flackbox.com/the-cisco-troubleshooting-methodology)

# Troubleshooting Approaches/Techniques

There are 4 key troubleshooting approaches/techniques you should use
1. **Work around the OSI model**
	1. Top down
		1. Application>Physical
	2. Bottom up
		1. Physical>Application
	3. Divide and Conquer
		1. Start in the middle
2. **Compare device configurations**
	1. Comparing configurations between backups and devices, running vs. startup, etc.
	2. Can identify *ad hoc* or *undocumented* changes that impacted performance
3. **Trace the path**
	1. Trace the path from source to destination
	2. Helpful in identifying [[Layer 1]] issues
4. **Check for broken components**
	1. Is the equipment is old?
	2. Was there a recent event (power surge, HVAC issue, liquid damage, etc) that might have caused an issue?
	3. Did a fiber cable get pinched or an Ethernet cable get cut?


# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources
[Troubleshooting Overview Cisco Systems](https://www.cisco.com/en/US/docs/internetworking/troubleshooting/guide/tr1901.html)
[The Cisco Troubleshooting Methodology - FlackBox](https://www.flackbox.com/the-cisco-troubleshooting-methodology)
