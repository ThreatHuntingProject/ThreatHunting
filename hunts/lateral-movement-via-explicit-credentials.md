# Windows Lateral Movement via Explicit Credentials

**Purpose**

Detect lateral movement in a Windows environment

**Data Required**

Windows event logs (ID 4648 or 552)

**Collection Considerations**

Check your domain audit policy to ensure that these events are being
generated.  Also, they are typically generated only on the host on
which the authentication occurs, so you need to collect from both
servers and user endpoints for full visibility.

**Analysis Techniques**

whitelisting / filtering

**Description**

Examine event logs for instances of explicit credentials being used
(as with the batch processes being spawned, users using the Runas
command or via pass-the-hash attacks).  Whitelist recurring instances
that are known to be authorized, and keep that whitelist up to date
over time.  Investigate any instances of explicit credential
authentication that may be left.

**Other Notes**

**More Info**

[Seek Evil, and Ye Shall Find: A Guide to Cyber Threat Hunting Operations](https://digitalguardian.com/blog/seek-evil-and-ye-shall-find-guide-cyber-threat-hunting-operations), Tim Bandos, Digital Guardian
