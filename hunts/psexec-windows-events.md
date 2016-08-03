#Psexec Windows Events

**Purpose**: 
Find instances of psexec service (remote command execution) on Windows sytems by examining event logs pertaining to access control for remote shares.

**Data Required**: 
Windows Event Logs (ID 5145)

**Collection Considerations**: 
None

**Analysis Techniques**: 
Filtering

**Description**

Look for Windows Event ID 5145, _A network share object was checked to
see whether client can be granted desired access_.  Filter for events
where the share is `IPC$` and the service is `PSEXECSVC-*`.  Cross
reference by examining the 5145 events for access to the `ADMIN$`
share for tool/file copies and execution events.

**Other Notes** Psexec is one of the most common mechanisms for
malicious lateral movement, but the tool is also occasionally used by
legitimate system administrators.

Event 5145 may not be enabled by default, as it requires "Detailed
File Auditing" (which can generate a *lot* of logs).

**More Info**

- [Tweet #1 by @jackcr](https://twitter.com/jackcr/status/733686717446656001)
- [Tweet #2 by @jackcr](https://twitter.com/jackcr/status/743587901468979202)
- [Tweet by @JPoForenso](https://twitter.com/JPoForenso/status/743663854601670656)

