#Detecting Lateral Movement in Windows Event Logs

**Purpose**: To detect authentication-based lateral movement in Windows envrionments

**Data Required**: Windows Security logs, specifically:

* Successful Logon (ID 4624)
* Failed Logon (ID 4625)
* Kerberos Authentication (ID 4768)
* Kerberos Service Ticket (ID 4776)
* Assignment of Administrator Rights (ID 4672)

**Collection Considerations**: Not all of these events are enabled by
  default, so you may need to change your audit policy

**Analysis Techniques**: Stack counting, outlier detection, visualization

**Description**
Make note of administrative attempts, visualize this activity and look for deviations from baseline in the number of attempts, the accounts involved in the attempts or the computers on which the attempts occur.

**Other Notes**
"Administrative" accounts includes any user with special rights, not necessarily only the Local or Domain "Administrator" accounts.

**More Info**

- [Detecting Lateral Movement in APTs: Analysis Approach on Windows Event Logs](https://www.first.org/resources/papers/conf2016/FIRST-2016-105.pdf), Shingo ABE, JPCERT/CC
