#Lateral Movement Detection via Process Monitoring

**Purpose**

Find threat actors moving laterally in the network by looking for examples of common techniques they use to orient themselves on new systems.

**Data Required**

Windows process creation logs (security event 4688) or other similar information (e.g., EDR logs)

**Collection Considerations**

The more endpoints and servers from which you collect process information, the more likely you are to be able to find threat actor activity.

**Analysis Techniques**

* Counting occurrences within a time window

**Description**

Several legitimate windows binaries executing within a specified time frame may indicate lateral movement.

As an adversary moves from machine to machine they will often want to know things like: who they are, what level of access do they have, what services are running on the machine, what other machines are around them… They will often determine this by using legitimate windows binaries.  When determining this information they will typically do this in minutes vs hours regardless if they are using a script or typing the commands on a command line.  Knowing this, we can use it to our advantage.  Again focusing on windows event logs and focusing on event codes 4688/592 try to identify the following:

* net.exe, ipconfig.exe, whoami.exe, nbtstat.exe...
* Cluster x number of processes executing within a 10 minute time frame.

For the data that is returned:

* identify the parent process and if it’s legitimate?
* What additional processes have executed on the machine within a 1 hour period and do any of those look suspicious?  If there are, are they owned by the same user?
* Are these spawned by the same process or process name?
* Are these processes all owned by the same user?
* Is there previous history of this activity?"

**Other Notes**

**More Info**

* [Hunting Lateral Movement](https://findingbad.blogspot.com/2016/08/hunting-lateral-movement.html)
* [CAR-2013-04-002: Quick execution of a series of suspicious commands](https://car.mitre.org/wiki/CAR-2013-04-002), MITRE Cyber Analytic Repository
* [CAR-2016-03-001: Host Discovery Commands](https://car.mitre.org/wiki/CAR-2016-03-001), MITRE Cyber Analytic Repository

