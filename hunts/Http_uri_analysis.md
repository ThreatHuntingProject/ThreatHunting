#Finding the Unknown with HTTP URI's

**Purpose**: Identify things signatures have not been created for in relation to network traffic behavior. 

**Data Required**: Proxy logs, IDS, web server logs

**Collection Considerations**: 

**Analysis Techniques**: Stack counting, String matching, tokenization, outlier detection, regex

**Description**

If you collect your proxy logs in a central location, similar to user agent analysis, you can perform queriest against the URI to identify patterns of malicious and suspicious activity leaving the environment. Ingress monitoring (proxy or web server logs) is also key for monitoring attackers performing attempts against web servers using suspicious requests. Similar to creating IDS signatures for detecting suspicious behavior, can perform that against mass amounts of data quickly to identify potential export of identifiable information.

Examples of types of strings to look for:

* OWASP Top 10
* Credit card strings
* Computer GUID
* Username GUID
* Base64 Encoded
* Encoded with something

**More Info**
