# Whaling Detection via Unusual Sender Domains

**Purpose**: "Whaling" is a variant of spearphishing, where the recipients are chosen because they are executives or senior management within the company. One way to detect these attacks is to look for messages destined to executive mailboxes from senders in domains with which the organization typically does not interact.

**Data Required**: Email logs containing both sender and recipient addresses

**Collection Considerations**: Collect email logs consisting of both the external -> internal messages as well as the internal -> internal messages.

**Analysis Techniques**: filtering, comparing list membership

**Description**
From the original source:

*To grasp this idea, we must establish parts of the sender and recipient email address. Using john.smith@contoso.com email address as an example, contoso.com would be the domain. And if the email was sent from john.smith@contoso.com to ashley.johnson@example.com then we would refer to contoso.com as the sender domain and example.com as the recipient domain.*

*Whaling Detection works by building a list of the sender domains sent to the high-profile employees and alerting on any emails when the sender domain is not found in these three sections:*

* Emails the high-profile employees composed themselves (recipient domain)
* Emails sent to non-high-profile employees
* Emails composed by non-high-profile employees (recipient domain)

**Other Notes**
Psuedocode for a whaling rule, also from the original source:

*ALERT: Recipient=HPE & Sender NOT IN (HPE_Composed_Domains OR NonHPE_Composed_Domains OR Sender_Domains_To_NonHPE)*

**More Info**

- [Whaling Detection](https://tech.target.com/2019/06/07/Whaling-Detection.html)
