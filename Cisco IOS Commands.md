## Basic Router/Switch configuration
```
! Copy files from one place to another
# copy [source] [destination]
! source and destination have the same options
!
! Configure an interface
Config# interface [interface]
!
! Use [Tab] to auto-complete the current partial command
! Use [?] to show all available switch options\
#copy ?
  flash: Copy from flash: file system
  ftp: Copy from ftp: file system
  running-config Copy from current system configuration
  scp: Copy from scp: file system
  startup-config Copy from startup configuration
  tftp: Copy from tftp: file system
!
asdfasdf

```


## Basic Router/Switch Configuration
1. Copy files from one place to another
	1. # copy (source) (destination)
		1. # copy ?
			1. [[IOS Storage Locations|flash]]: Copy from [[IOS Storage Locations|flash]]: file system
			2. ftp: Copy from ftp: file system
			3. running-config Copy from current system configuration
			4. scp: Copy from scp: file system
			5. startup-config Copy from startup configuration
			6. tftp: Copy from tftp: file system
2. Show the details of the running config
	1. # sho run ?
3. Configure an interface
	1. Config# interface (interface ID)
4. Escalate Privileges
	1. (Enter)
	2. > enable
		1. # configure terminal
			1. Config# (feature being configured)
5. 