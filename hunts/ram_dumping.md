#RAM Dumping

**Purpose**: Examine memory dumps of an individual system, looking for signs of malware or other malicious activities

**Data Required**: RAM dumps (typically HUGE)

**Collection Considerations**: Require a specialized tool (e.g., Volatility)

**Description**

RAM dumps of running systems can often contain lots of interesting information, such as lists of running processes, open ports, executable images and logged on users.  Using various tools, you can extract these types of information and potentially look for signs of malicious activities.

Checking for "known-bad" is one obvious application.  D. Sharpe suggests also looking for signs of BIOS or firmware implants (detecting tampering with the interrupt table and checking uppermost addresses of real-mode memory).  

**Other Notes**

Better description needed here.

**More Info**

* [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)
* "Art of Memory Forensics", Ligh, Case, Levy, Walters, Wiley Publishing, 2014 (page 75 addresses BIOS/firmware attacks)

