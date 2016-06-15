#Suspicious Process Creation via Windows Event Logs

**Purpose**: Find attacker tools in use 

**Data Required**: Windows process creation logs (Event 4688 & 592)

**Collection Considerations**: Collect these from every host in the domain

**Analysis Techniques**: stack counting

**Description**

This is based on a set of tweets by Jack Crook (@jackcr):

"Attackers need to execute tools. Look at Windows Event ID's 4688/592. Stack and look for outliers. Group by execution time and user."

"Finding webshells: Look at process creations (4688/592) that are spawned from users that own webserver processes."

"One of my favorites is that knowing when attackers bring tools in with them they will likely not execute them very often in a 24hr time period. Looking at precess creations with a hard limit of executing x number of times in a day and ordering by by file path. Can start to weed out, either manually or automated, those processes that have been validated as legit"

**Other Notes**

Event 4688 is even more valuable if logging policy is set to record the entire command line.

**More Info**

- [Tweet by @jackcr #1](https://twitter.com/jackcr/status/707215101007413248)
- [Tweet by @jackcr #2](https://twitter.com/jackcr/status/707551910031728640)
- [Tweet by @jackcr #3](https://twitter.com/jackcr/status/707247278118084608)
- [Tweet by @jackcr #4](https://twitter.com/jackcr/status/707247524516651008)
- [Tweet by @jackcr #5](https://twitter.com/jackcr/status/707247746462384129)

