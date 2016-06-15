#Search for Rogue Listeners

**Purpose**: Find malicious programs that are listening to network ports

**Data Required**: Netstat data (*netstat -nabo*) or equivalent from local host

**Collection Considerations**: Requires some sort of agent to collect this data on a regular basis

**Analysis Techniques**: Stack counting

**Description**

Extract src & dest host/port fields from all *netstat* data, as well as the full path name for the associated executable.  Look for:

* More than one process name bound to the same port on the same system (the ones with the smallest number of occurrences on each system are suspicious)
* For all Internet-accessible servers, which ports show up only once (or just a few times)?
* For all Internet-accessible servers, how many binaries show up only once (or just a few times)?
* Track new listeners over time for each system, use this as a baseline to refine future hunts.

**More Info**

* [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)


