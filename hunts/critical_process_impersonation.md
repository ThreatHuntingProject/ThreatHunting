# Finding Malware Process Impersonation via String Distance

**Purpose**

Finds malware attempting to hide execution by running with names which are confusingly similar to legitimate system processes.

**Data Required**

Endpoint process creation data

**Collection Considerations**

None

**Analysis Techniques**

Scripting

**Description**

A popular technique for hiding malware running on Windows systems is to give it a name that's confusingly similar to a legitimate Windows process, preferably one that is always present on all systems. Using a _string similarity_ algorithm ([Damerau-Levenshtein](https://en.wikipedia.org/wiki/Damerau%E2%80%93Levenshtein_distance) distance), we can compare the names of running processes to a set of defined Windows system processes to look for this sort of impersonation.

**Other Notes**

None

**More Info**

- [Hunting for Malware Critical Process Impersonation](http://detect-respond.blogspot.com/2016/11/hunting-for-malware-critical-process.html)