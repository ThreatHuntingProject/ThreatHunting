#Suspicious Process Creation via Windows Event Logs

**Purpose**

Find attacker tools in use 

**Data Required**

Windows process creation logs (Event 4688 & 592)

**Collection Considerations**

Collect these from every host in the domain.  If you have additional
endpoint data collection tools that can log data about process
execution (e.g. Microsoft Sysmon, Carbon Black, etc) you may be able
to similar analyses with equivalent data.

**Analysis Techniques**

stack counting

**Description**

Search all process creation log entries and look for:

* `svchost.exe` processes that are not children of `services.exe`
* Processes created by binaries in unsual locations, such as
	* `%windows%\fonts`
	* `%windows%\help`
	* `%windows%\wbem`
	* `%windows%\addins`
	* `%windows%\debut`
	* `%windows%\system32\tasks`
* Known attacker tool names, such as
	* `rar.exe`
  	* `psexec.exe`
  	* `whoami.exe`

* Processes that launched very few times during a 24 hour period


The following are based on a set of tweets by Jack Crook (@jackcr):

"Attackers need to execute tools. Look at Windows Event ID's 4688/592. Stack and look for outliers. Group by execution time and user."

"Finding webshells: Look at process creations (4688/592) that are spawned from users that own webserver processes."

"One of my favorites is that knowing when attackers bring tools in with them they will likely not execute them very often in a 24hr time period. Looking at precess creations with a hard limit of executing x number of times in a day and ordering by by file path. Can start to weed out, either manually or automated, those processes that have been validated as legit"


* Legitimate windows binaries executing within a specified time frame may indicate lateral movement

"As an adversary moves from machine to machine they will often want to know things like: who they are, what level of access do they have, what services are running on the machine, what other machines are around them… They will often determine this by using legitimate windows binaries.  When determining this information they will typically do this in minutes vs hours regardless if they are using a script or typing the commands on a command line.  Knowing this, we can use it to our advantage.  Again focusing on windows event logs and focusing on event codes 4688/592 try to identify the following:

1. Net.exe, ipconfig.exe, whoami.exe, nbtstat.exe...
2. Cluster x number of processes executing within a 10 minute time frame.

For the data the get’s returned:

1. identify the parent process and if it’s legitimate?
2. What additional processes have executed on the machine within a 1 hour period and do any of those look suspicious?  If there are, are they owned by the same user?
3. Are these spawned by the same process or process name?
4. Are these processes all owned by the same user?
5. Is there previous history of this activity?"

**Other Notes**

Event 4688 is even more valuable if logging policy is set to record
the entire command line (some of these suggestions require that info).
Review your domain audit policies and/or supplement with additional
process logging as necessary.  Sysmon is a very good free tool that
can do nearly anything you'd need.



**More Info**

- [Tweet by @jackcr #1](https://twitter.com/jackcr/status/707215101007413248)
- [Tweet by @jackcr #2](https://twitter.com/jackcr/status/707551910031728640)
- [Tweet by @jackcr #3](https://twitter.com/jackcr/status/707247278118084608)
- [Tweet by @jackcr #4](https://twitter.com/jackcr/status/707247524516651008)
- [Tweet by @jackcr #5](https://twitter.com/jackcr/status/707247746462384129)
- [Seek Evil, and Ye Shall Find: A Guide to Cyber Threat Hunting Operations](https://digitalguardian.com/blog/seek-evil-and-ye-shall-find-guide-cyber-threat-hunting-operations), Tim Bandos, Digital Guardian
- https://findingbad.blogspot.com/2016/08/hunting-lateral-movement.html

