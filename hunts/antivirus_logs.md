# Finding Known-Bad in Antivirus Logs

**Purpose**: Identify things that the AV system has found that you particularly care about

**Data Required**: Endpoint security logs (AV); List of "bad things" to look for.

**Collection Considerations**: 

**Analysis Techniques**: String matching

**Description**

If you collect all your endpoint security logs in one place, you can search them for specific strings that correspond to things you're particularly interested in finding.  In other words, things you may want to treat as _more important_ than normal alerts the endpoint security tool may already be creating.  

Examples of types of strings to look for:

* Known webshell filenames
* Anything running under a system directory (%WINDOWS%, %RECYCLER%) or other unusual locations (the webroot)
* AV "street names" you are concerned about
* Packed executables (if this information is logged)
* Known attacker tools (cred dumpers, scanners, etc)
* Any detection with the string "dropper" in the name

**More Info**

* [Intrusion Hunting for the Masses - David Sharpe (HackMiami 2016)](https://www.youtube.com/watch?v=YLgycMCPo4c)
* [Seek Evil, and Ye Shall Find: A Guide to Cyber Threat Hunting Operations](https://digitalguardian.com/blog/seek-evil-and-ye-shall-find-guide-cyber-threat-hunting-operations), Tim Bandos, Digital Guardian


