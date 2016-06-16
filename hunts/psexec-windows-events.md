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
Look for Windows Event ID 5145, _A network share object was checked to see whether client can be granted desired access_.  Filter for events where the share is _IPC$_ and the service is _PSEXECSVC-*_.

**Other Notes**
Psexec is one of the most common mechanisms for malicious lateral movement, but the tool is also occasionally used by legitimate system administrators.

**More Info**

- [Tweet by @jackcr](https://twitter.com/jackcr/status/733686717446656001)


