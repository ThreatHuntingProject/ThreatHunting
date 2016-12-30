# Identify Suspicious Command Shells

**Purpose**: To identify instances of running command shells which may indicate threat actor activity.

**Data Required**: Process execution data (Sysmon, Carbon Black, etc)

**Collection Considerations**: Collect from all systems in the domain

**Analysis Techniques**: Baselining, stack counting

**Description**

Look for instances of `cmd.exe` or `powershell.exe` where any of the following are true:

* The parent process does not normally spawn a command shell (e.g., `word.exe`)
* The command shell executed `reg.exe` or other command not normally used by end-users
* The command shell was launched by a running service or by `winlogon.exe`
* The command shell was started by WinRM ("wsmprovhost.exe" started by "svchost.exe" may indicate remote PowerShell execution)

**Other Notes**

The same techniques may be useful when applied to more than just command shell binaries.  For example, you might want to search for any instance of a service launching `wmic.exe`.

**More Info**

* [CAR-2013-02-003: Processes Spawning cmd.exe](https://car.mitre.org/wiki/CAR-2013-02-003), MITRE Cyber Analytic Repository
* [CAR-2013-03-001: Reg.exe called from Command Shell](https://car.mitre.org/wiki/CAR-2013-03-001), MITRE Cyber Analytic Repository
* [CAR-2014-05-002: Services launching Cmd.exe](https://car.mitre.org/wiki/CAR-2014-05-002), MITRE Cyber Analytic Repository
* [CAR-204-11-002: Outlier Parents of Cmd](https://car.mitre.org/wiki/CAR-2014-11-002), MITRE Cyber Analytic Repository
* [CAR-2014-11-004: Remote PowerShell Sessions](https://car.mitre.org/wiki/CAR-2014-11-004), MITRE Cyber Analytic Repository
* [CAR-2014-11-008: Command Launched from WinLogon](https://car.mitre.org/wiki/CAR-2014-11-008), MITRE Cyber Analytic Repository

