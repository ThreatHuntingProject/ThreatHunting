#RDP External Access

**Purpose**: Identify abnormal incoming RDP requests 

**Data Required**: RDP connection / authorization logs that capture client IP address or client computer name. Data that contains client computer name is preferred over client IP address because it allows the analyst to identify individual clients connecting from the same node (e.g., a VPN node). Useful sources for this data are the Bro RDP analyzer and Windows Event IDs 4624 (Type 10) and 4778.

**Collection Considerations**: Bro requires a production NSM deployment, Windows events may be easier to collect for many organizations. 

**Analysis Techniques**: Stack counting, baselining / outlier detection

**Description**

Identifying abnormal incoming RDP requests has two primary goals: to identify compromised user credentials (e.g., an attacker may use compromised credentials to access the corporate VPN) or to identify internet-facing assets running the RDP service that are being illegitimately accessed. Identifying these requests requires a basic level of friendly intelligence-- at minimum, analysts should be able to identify incoming RDP connections that occur at the edge of the network and ideally, analysts should be able to differentiate artifacts related to legitimate users from foreign users. 

Baselining is the most effective technique for identifying abnormal requests-- specifically, baselining when a client computer accesses the network and the user credentials used by the client can be useful when identifying outliers. If a client accesses the network at an abnormal time or if user credentials are used on a client that has never been seen on the network, then they may be worth investigating. 

Stack counting can be effective if the analyst can easily identify anomalies in the data set. For example, if an analyst is familiar with the workstation naming convention used on their network, then they may be able to identify when an outside client accesses the network. Stack counting the client computer names for incoming requests is a good start to identifying this type of access. 

**More Info**

* [Hunting Through RDP Data - Josh Liburdi (BroCon 2015)](https://www.youtube.com/watch?v=mOV_9YMgYZw)
* [CAR-2016-04-005: Remote Desktop Login](https://car.mitre.org/wiki/CAR-2016-04-005), MITRE Cyber Analytic Repository
