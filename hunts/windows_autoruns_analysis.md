#Autoruns Analysis

**Purpose**: Find malware persistence by examining common mechanisms across a network

**Data Required**: List of programs configured to start at boot/logon time on each endpoint

**Collection Considerations**: MS Sysinternals' `autorunsc.exe` is the most common way to collect this from a host

**Analysis Techniques**: Stack counting, string matching, outlier detection

**Description**

Gather autoruns data from endpoints across the network and look for:

* Executable starting out of `c:programdata`, recycle bin, appdata area, `%temp%`
* Unsigned executables
* Shortest / longest filenames 
* GUID filenames
* Rare executable filenames or directories


**More Info**

* [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)
* [CAR-2013-01-002: Autorun Differences](https://car.mitre.org/wiki/CAR-2013-01-002), MITRE Cyber Analytic Repository
