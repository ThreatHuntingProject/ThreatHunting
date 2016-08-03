#Windows Driver Analysis

**Purpose**: Find malware running in Windows drivers across a network

**Data Required**: List of drivers loaded on each endpoint

**Collection Considerations**: Typically use the `driverquery` command on each host.

**Analysis Techniques**: Stack counting

**Description**

Examine driver entries for:

* Impossible, zeroed or garbage link dates
* Stack each binary image and look for unusual link dates
* Unusual filenames or locations of binaries
* Rare descriptions
* Incorrect descriptions (grammar, typos, punctuation, etc)
* Rare display names
* Missing, invalid or unusual digital signatures

**More Info**

* [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)



