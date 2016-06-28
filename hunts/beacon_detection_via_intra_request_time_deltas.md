#Beacon Detection via Intra-Request Time Deltas

**Purpose**: Find regular HTTP beaconing behavior which may indicate malware C2

**Data Required**: HTTP proxy logs

**Collection Considerations**: 

**Analysis Techniques**: Visualization (Bar graphs)

**Description**

Malware C2 often utilizes regular request intervals ("beacons") to maintain control with the attacker's infrastructure.  By examining the intra-request times between requests to the same resource by the same source IP and visualizing the results, you can look for patterns of regular activity.

**Other Notes**


**More Info**

- [Detecting Malware Beacons Using Splunk](http://pleasefeedthegeek.wordpress.com/2012/12/20/detecting-malware-beacons-using-splunk/)

- [Tweet by @jackcr](https://twitter.com/jackcr/status/747786867093946368)
