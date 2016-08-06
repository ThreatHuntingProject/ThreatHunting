#C2 via Dynamic DNS 

**Purpose**: Identify potential C2 activity

**Data Required**

Outgoing logs that contain info about domains
visited by internal clients, such as DNS query or HTTP proxy logs.

You will also need a list of dynamic DNS provider domain names.

**Collection Considerations**

None

**Analysis Techniques**
Filtering, stack counting

**Description**

Isolate the log entries that contain domains hosted on dynamic DNS
providers.  Look for sites visited by a low number of unique hosts (IP
addresses). Utilize a lookup or feed of known dynamic DNS (DDNS) domains
to query against data in a SIEM or log aggregator. 

**Other Notes**

In many business environments, _any_ access to a dynamic DNS provider
may be at least somewhat suspicious.

**More Info**

- [Seek Evil, and Ye Shall Find: A Guide to Cyber Threat Hunting Operations](https://digitalguardian.com/blog/seek-evil-and-ye-shall-find-guide-cyber-threat-hunting-operations), Tim Bandos, Digital Guardian
- [www.malwaredomains.com Dynamic DNS domain list](http://mirror1.malwaredomains.com/files/dynamic_dns.txt), Malwaredomains.com

