#Internet-Facing HTTP Request Analysis

**Purpose**: Identify common patterns of HTTP-based attacks

**Data Required**: Internet-facing HTTP server logs

**Collection Considerations**: 

**Analysis Techniques**: Stack counting, Visualization, Outlier detection

**Description**

Stack server logs by (Src IP, HTTP server, URI) tuples and look for repeated requests for the same resource.  Large numbers of request could indicate:

* Attempts to create a working exploit for a supposed vulnerability
* Attempts to use a web shell embedded in the web content directory

Using _a priori_ knowledge or by examining file extensions, Identify URI resources that are likely to contain calls to SQL (or similar) backend application layers.  For each unique URI, gather all the the values for the HTTP response sizes.  Using visualization or statistical outlier detection of the response sizes,

* identify those which are significantly larger than the others. These may be indicators of successful SQL injection (e.g., database dumps or other unusual information being sent via the HTTP responses).

**Other Notes**

Using the response sizes, also identify those which are significantly smaller than the others.  These may be indicators of injection errors that cause the app to exit prematurely and send less data than normal.  Or maybe those which are bigger, indicating success!  Regardless, repeated requests for the same resource probably would result in similar-sized responses, so significant variations would be interesting the look into.


