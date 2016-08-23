# Finding Golden and Silver Tickets

**Purpose**

Identify suspicious TGT (Golden) and TGS (Silver) tickets by comparing the MaxTicketAge from the domain policy to the difference in the StartTime and EndTime of the cached authentication ticket.

**Data Required**

Remote Access to collect susicious tickets OR  
Schedule task to write possible bad tickets to application event log for log/SIEM review

**Collection Considerations**

Consider running local scripts and collecting the application event log rather than a scan to reduce noise
See [here](https://github.com/spohara79/TGT---Golden-Silver-Ticket)

**Analysis Techniques**: 

Comparative time analysis of domain policy vs cached tickets

**Description**

* Retrieve the Kerberos MaxTicketAge from the GPO / Domain Policy
* Use `klist.exe sessions` to view the cached sessions
    * view the TGT or TGS tickets using `klist tgt -li <sessionid>` or `klist tickets -li <sessionid`
        * Extract the EndTime and StartTime values
* Subtract the EndTime from StartTime and compare that value against the configured MaxTicketAge
    * The MaxTicketAge defaults to 10 hours, many TGT/TGS Golden/Silver Tickets are set for a period of years..

**Other Notes**    

From [ADSecurity](https://adsecurity.org/?p=1515)

***SILVER TICKET DETECTION***    

Silver Ticket events may have one of these issues:  
The Account Domain field is blank when it should be DOMAIN  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  
Event ID: 4624 (Account Logon)  
Account Domain is FQDN & should be short domain name  
Account Domain:        LAB.ADSECURITY.ORG   [ADSECLAB]  
Event ID: 4634 (Account Logoff)  
Account Domain is blank & should be short domain name  
Account Domain:        _______________   [ADSECLAB]  
Event ID: 4672 (Admin Logon)  
Account Domain is blank & should be short domain name  
Account Domain:        _______________   [ADSECLAB]  
 
***GOLDEN TICKET DETECTION***

Golden Ticket events may have one of these issues:  
The Account Domain field is blank when it should be DOMAIN  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  
Event ID: 4624 (Account Logon)  
Account Domain is FQDN & should be short domain name  
Account Domain:        LAB.ADSECURITY.ORG   [ADSECLAB]  
   
Event ID: 4672 (Admin Logon)  
Account Domain is blank & should be short domain name  
Account Domain:        _______________   [ADSECLAB]  
  
MS14-068 Exploit Ticket Detection   
MS14-068 events may have one of these issues:  
The Account Domain field is blank when it should be DOMAIN  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  
Account Name is a different account from the Security ID.  
  
PYKEK Events  
Event ID: 4624 (Account Logon)  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  
Account Name is a different account from the Security ID  
 Event ID: 4672 (Admin Logon)  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  
Account Name is a different account from the Security ID  
Event ID: 4768 (Kerberos TGS Request)  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  
  
KEKEO Events  
Event ID: 4624 (Account Logon)  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  
 
Event ID: 4672 (Admin Logon)  
Account Domain is blank & should be DOMAIN.  
  
Event ID: 4768 (Kerberos TGS Request)  
The Account Domain field is DOMAIN FQDN when it should be DOMAIN.  

**More Info**

[Powershell Scripts for Golden and Silver Ticket Hunt](https://github.com/spohara79/TGT---Golden-Silver-Ticket)  
[Detecting Golden and Silver Tickets - ADSecurity](https://adsecurity.org/?p=1515)
