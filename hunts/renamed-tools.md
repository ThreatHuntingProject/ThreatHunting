# Tool Renaming

**Purpose**

Identify common tools that attackers routinely rename

**Data Required**

* HIPS or other related host monitoring solution that logs file metadata.
* Process execution data (e.g., Sysmon, Carbon Black, etc) 

**Collection Considerations**

Collect from all endpoints and servers

**Analysis Techniques**: 

String matching, file hash analysis

**Description**

When an adversary gains access to your network they will often bring a set of tools in with them to facilitate lateral movement, credential theft and data exfiltration.  By analyzing the FileDescription metadata field of a PE file, it is possible to uncover files that have been renamed by an attacker.

* An example would be when an attacker renames the SysInternals tool PsExec.exe
* Identify the FileDescription 'Execute Processes Remotely' where the filename does not equal PsExec.exe.

Identify common windows executable names or names that are 1-2 characters in length.  Also pay attention to files that reside in the ADMIN$ or IPC$ shares.

Look for executable files which have the same hash (MD5, SHA1) but different paths and/or filenames.  

Look for previously-unseen binaries that have arguments in common with other known tools (for example, any process with 'sekurlsa' in the command line is likely to be Mimikatz).

**More Info**

* [CAR-2013-05-009: Running executables with same hash and different names](https://car.mitre.org/wiki/CAR-2013-05-009), MITRE Cyber Analytic Repository
* [CAR-2013-07-001: Suspicious Arguments](https://car.mitre.org/wiki/CAR-2013-07-001), MITRE Cyber Analytic Repository
* [CAR-2013-07-005: Command Line Usage of Archiving Software](https://car.mitre.org/wiki/CAR-2013-07-005), MITRE Cyber Analytic Repository

