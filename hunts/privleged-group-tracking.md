#Privileged Group Tracking

**Purpose**

Detect potential privilege escalation attempts

**Data Required**

Windows event logs (ID 4728, 4732, 4756)

**Collection Considerations**

Event 4728 and 4756 are only logged on domain controllers.  Event 4732
may be logged on either the domain controller or an individual
computer, depending on whether the group is a domain or a local
group. You should ideally collect ID 4732 events on all computers in
the domain for full visibility.

**Analysis Techniques**

None

**Description**

Adding a non-privileged account to a privileged group is a common
method for attackers to gain more access to a compromised system or
domain.  In most environments, this operation is not common, so any
occurrences of the listed event types should be investigated.

**Other Notes**

**More Info**

[Seek Evil, and Ye Shall Find: A Guide to Cyber Threat Hunting Operations](https://digitalguardian.com/blog/seek-evil-and-ye-shall-find-guide-cyber-threat-hunting-operations), Tim Bandos, Digital Guardian


