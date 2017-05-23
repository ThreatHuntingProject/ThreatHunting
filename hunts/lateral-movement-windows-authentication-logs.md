# Detecting Lateral Movement in Windows Event Logs

**Purpose**

To detect authentication-based lateral movement in Windows envrionments

**Data Required**

Windows Security logs, specifically:

* Successful Logon (ID 4624)
* Failed Logon (ID 4625)
* Kerberos Authentication (ID 4768)
* Kerberos Service Ticket (ID 4776)
* Assignment of Administrator Rights (ID 4672)
* Unknown username or password (ID 529)
* Account logon time restriction violation (ID 530)
* Account currently disabled (ID 531)
* User account has expired (ID 532)
* User not allowed to logon to the computer (ID 533)
* User has not been granted the requested logon type (ID 534)
* The account's password has expired (ID 535)
* The NetLogon component is not active (ID 536)
* The logon attempt failed for other reasons (ID 537)
* Account lockout (ID 539)

**Collection Considerations**

Not all of these events are enabled by default, so you may need to
change your audit policy

**Analysis Techniques**

Stack counting, outlier detection, visualization

**Description**

Make note of administrative attempts, visualize this activity and look for deviations from baseline in the number of attempts, the accounts involved in the attempts or the computers on which the attempts occur.

Look for instances where multiple users are logged onto an end-user workstation simultaneously or within a relatively short period of time, where the same user account is logged onto more than one host, or where a network login references a non-domain account on the target system.

**Other Notes**

"Administrative" accounts includes any user with special rights, not necessarily only the Local or Domain "Administrator" accounts.

**More Info**

* [Detecting Lateral Movement in APTs: Analysis Approach on Windows Event Logs](https://www.first.org/resources/papers/conf2016/FIRST-2016-105.pdf), Shingo ABE, JPCERT/CC
* [Seek Evil, and Ye Shall Find: A Guide to Cyber Threat Hunting Operations](https://digitalguardian.com/blog/seek-evil-and-ye-shall-find-guide-cyber-threat-hunting-operations), Tim Bandos, Digital Guardian
* [CAR-2013-02-008: Simultaneous Logons on a Host](https://car.mitre.org/wiki/CAR-2013-02-008), MITRE Cyber Analytic Repository
* [CAR-2013-02-012: User Logged in to Multiple Hosts](https://car.mitre.org/wiki/CAR-2013-02-012), MITRE Cyber Analytic Repository
* [CAR-2016-04-004: Successful Local Account Login](https://car.mitre.org/wiki/CAR-2016-04-004), MITRE Cyber Analytic Repository



