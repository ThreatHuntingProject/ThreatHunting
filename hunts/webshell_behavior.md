# Webshell Behavior

**Purpose**

Identify actions taken by attacker when a webshell is initially placed on a webserver

**Data Required**

Windows security event logs (4688/592 events), HIPS or other related host monitoring solution that provides audit information about process creation

**Collection Considerations**

Collect from all webservers

**Analysis Techniques**: 

Base analysis on bucket times and file / process ownership.

**Description**

"When a web server gets compromised there are some typical things that will likely occur (Though not in every case). 

* A new file will be placed on the web server with a web file extension and in a web accessible directory. 
* Commands will be executed from the webshell. (cmd.exe, powershell.exe…) 
* Additional tools will be uploaded to the web server. (Look for newly created files with extensions of .zip, .rar, .7z, .exe…)

Looking for at least 2 of these occurrences from the above in a 15 minute window can help identify suspicious behavior that may need investigating.  Multiple log sources may need to be incorporated for this, but the work in doing so can be well worth the effort."

**More Info**

* [My Thoughts on Threat Hunting](https://findingbad.blogspot.com/2016/07/my-thoughts-on-threat-hunting.html) (Jack Crook)
