#Windows Prefetch Cache Analysis

**Purpose**: Identify malware or other suspicious executables that ran on a system.

**Data Required**: Windows prefetch cache data

**Collection Considerations**: Requires a special tool to convert binary file format to something we can consume (e.g., Nirsoft `WinPrefetchView`. Probably needs an agent.

**Analysis Techniques**: Stack counting, outlier detection

**Description**

Whenever any process executes on a Windows system, Windows writes an entry to the Prefetch cache.  This actually supports an internal mechanism that tries to keep frequently-used binaries quickly accessible to increase performance, but it's good for hunting because it records info about what commands were recently run. 

This capability is present on all Windows versions starting with XP, though it is not enabled by default on Windows Server, so mostly this will apply to user endpoints.  Also, for hardware reasons, it's usually disabled for systems with SSDs.  

From XP to Windows 7, the default limit was 128 files.  This was increased to 1024 starting with Windows 8.

Here's a sample prefetch record (format is tool-dependent, but they should all include the same info):


	Filename     : DLLHOST.EXE-61F58501.pf 
	Created Time     : 9/9/2015 6:15:41 PM 
	Modified Time     : 9/9/2015 6:15:41 PM
	File Size     : 5,726
	Process EXE     : DLLHOST.EXE
	Process Path     : C:WindowsSystem32dllhost.exe
	Run Counter     : 1
	Last Run Time     : 9/9/2015 6:15:08 PM
	Missing Process     : No 


Stack the various fields and look for:

* Unusual filenames and process EXE values (be sure to ignore the "-61F58501.pf" part, which is not relevant)
* Same names but with unusual create/modify times or file sizes
* Known-bad filenames & locations
* Unusual executable locations
* Unusually short / long names in filename or process EXE fields

These are often suspicious, especially if the run count is very low (like 1).

Order commands on each host by run time and look for:

* Unusual combinations of commands (e.g., "net" followed closely by "ping", "at" or similar).

**Other Notes**

Order commands on each host by run time and look for:

* Commands run at unusual times for each host

**More Info**

* [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)


