#EMET Log Mining

**Purpose**: Identify potential 0-day exploits by looking for things blocked by EMET

**Data Required**: Windows Application Event logs (which contain EMET logs)

**Collection Considerations**: 

**Analysis Techniques**: 

**Description**

Window's Enhanced Mitigation Experience Toolkit (EMET) is a set of technologies that monitor for and block certain conditions that commonly arise as the result of common exploit patterns.  It's commonly used on endpoints (but is also available on servers).  

The idea here is to examine the EMET logs to find things that it has blocked (processes it has killed before they could become dangerous).  These may be simple bugs in legit applications, or they could be indications of exploit attempts.

**Other Notes**

It's not clear what actual analysis techniques might be useful here yet, short of simply examining every EMET log individually. Need more research on this one.

**More Info**

* [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c),  David Sharpe (HackMiami 2016)


