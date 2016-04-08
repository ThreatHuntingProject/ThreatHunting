#HTTP User-Agent Analysis

**Purpose**: Identify malware by analyzing the User-Agent strings they present

**Data Required**: HTTP proxy data; list of known-bad UAs (optional)

**Collection Considerations**: 

**Analysis Techniques**: Stack counting, String matching, tokenization, outlier detection

**Description**

* Stack the entire UA string and look for rare occurrences.  There may be a LOT of these, though. Every web plugin changes the UA string a bit, but that doesn't mean there's anything evil.
* Consider more detailed analysis, including
    * tokenizing the string and focusing on strings with the lowest number of tokens, most unique tokens, or some combination
    * Looking for abnormally short or long strings
* Look for list of known-bad UAs

**Other Notes**

Consider also doing this type of analysis for _incoming_ HTTP transactions (in server logs) to identify potential recon or attack activity.

* Intrusion Hunting for the Masses - David Sharpe (DerbyCon 2015)
* [http://www.secureworks.com/cyber-threat-intelligence/threats/threat-group-3390-targets-organizations-for-cyberespionage/]()
* [http://blog.didierstevens.com/2015/05/11/detecting-network-traffic-from-metasploits-meterpreter-reverse-http-module/]()

