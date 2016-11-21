#Finding C2 in Network Sessions

**Purpose**

Identify anomalous network sessions that may indicate command and control (C2) activity

**Data Required**

Network session data, including IP-to-IP metadata, port use, session length/duration

**Collection Considerations**

Data can be collected from a variety of systems, including firewalls, NSM sensors (Bro), and SiLK

**Analysis Techniques**

Stacking, baselining

**Description**

Identifying network sessions that may indicate C2 activity can be achieved in multiple ways. One of the simplest is to analyze specific types of data associated with network sessions. These include outbound IP-to-IP connections, destination IP address connectivity, destination port use, and session length.

Stacking is a relatively easy way to analyze the data described above. To do this, you want to isolate network data to outbound sessions that happen at the border of your network and stack the number of occurrences for each type or combination of data. For example, to stack IP-to-IP connections, isolate the data to outbound sessions and count the number of unique connections between the source IP (internal host) and the destination IP (external host); for destination port use, isolate the data and stack the number of occurrences of each destination port. In large networks, you may need to isolate the data to specific internal subnets or classes of hosts.  

C2 can appear anywhere in the stacked results, but as a start, it may be useful to investigate activity that appears at the top or bottom of the result set-- these top and bottom outliers represent anomalous data and may be C2. 

**More Info**

_None at this time._