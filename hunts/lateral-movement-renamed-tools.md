# Tool Renaming

**Purpose**

Identify common tools that attackers routinely rename

**Data Required**

HIPS or other related host monitoring solution that logs file metadata

**Collection Considerations**

Collect from all endpoints and servers

**Analysis Techniques**: 

Idnetify common windows executable names or names that are 1-2 characters in length

**Description**

When an adversary gains access to your network they will often bring a set of tools in with them to facilitate lateral movement, credential theft and data exfiltration.  By analyzing the FileDescription metadata field of a PE file, it is possible to uncover files that have been renamed by an attacker.

* An example would be when an attacker renames the SysInternals tool PsExec.exe
* Identify the FileDescription 'Execute Processes Remotely' where the filename does not equal PsExec.exe.
