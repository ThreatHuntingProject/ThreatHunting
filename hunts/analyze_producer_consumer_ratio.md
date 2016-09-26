#Producer-Consumer Ratio for Detecting Data Exfiltration

**Purpose**: Find changes in traffic flows that indicate exfil

**Data Required**: session data (argus, netflow/ipfix, or bro-logs)

**Collection Considerations**: 

**Analysis Techniques**: Identify changes in host roles, and investigate. PCR is
a normalized metric of traffic ratios and from a host ranging from -1 to 1. 

|  PCR | host role |
| ---: | --------- |
|  1.0 | pure push - FTP upload, multicast, beaconing |
|  0.4 | 70:30 export - Sending Email |
|  0.0 | Balanced Exchange - NTP, ARP probe |
| -0.5 | 3:1 import - HTTP Browsing |
| -1.0 | pure pull - HTTP Download |
    
**Description**

The Producer-Consumer Ratio metric introduced at [FlowCON](http://qosient.com/argus/presentations/Argus.FloCon.2014.PCR.Presentation.pdf) by Carter Bullard and John Gerth is defined as:

          ( SrcApplicationBytes - DstApplicationBytes )
    PCR = ---------------------------------------------
          ( SrcApplicationBytes + DstApplicationBytes )

where:

    Application Bytes = (Total Bytes ⎼ Sum( L[2,3,4] Headers )) - Retrans Bytes

DNS is less noisy than HTTP for this metric, and is a possible exfil channel. A
positive shift in PCR for DNS traffic may indicate DNS Exfil.


**Other Notes**


**More Info**

- [PCR - A New Flow Metric, FloCon 2014](http://qosient.com/argus/presentations/Argus.FloCon.2014.PCR.Presentation.pdf)
- [Leveraging Metadata And Machine Learning To Enhance Intrusion Analysis](http://spotidoc.com/doc/367670/leveraging-metadata-and-machine-learning)
- [Github: reservoirlabs/bro-producer-consumer-ratio](https://github.com/reservoirlabs/bro-producer-consumer-ratio)
- [Detecting Data Staging & Exfil Using the Producer-Consumer Ratio](http://detect-respond.blogspot.com/2016/09/detecting-data-staging-exfil-using-PCR-shift.html)
