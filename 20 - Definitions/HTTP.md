---
aliases:
  - HTTPS
tags:
  - defs_ccna
dg-publish: true
---
### HTTP
- Hypertext Transfer Protocol is used to share and request information

#### HTTP Requests

##### HTTP Verbs
1. GET
	1. Retrieves data from the server
	2. Idempotent
	3. Includes sensitive information in the [[URI]], which can be logged
2. PUT
	1. Updating an existing resource or create a new resource of it doesn't exist
	2. Idempotent
3. POST
	1. Creating a new resource
	2. Not idempotent (multiple identical requests results in different outcomes)
	3. Does not include form data in the request *URI*; instead, form data is encoded in a [[URL]], and calls a function on the server to process the information
4. HEAD
	1. Retrieving metadata about a source without fetching the actual data
		   	1. HTML standard prevents HEAD requests from containing message body/form data
		   	2. Typically only used to extract header information or test HTML links
	2. Idempotent


#### HTTP Response Codes
1. **1xx** - Informational
	1. The request was received, continuing process 
2. **2xx** - Successful
	1. The request was successfully received, understood, and accepted
3. **3xx** - Redirection
	1. Further action needs to be taken in order to complete the request
4. **4xx** - Client Error
	1. The rest contains bad syntax or could not be fulfilled
5. **5xx** - Server Error
	1. The server failed to fulfill an apparently valid request



# Metadata
### OSI or TCP/IP Layer

### CCNA Exam Topic

### Contributors

### Sources

