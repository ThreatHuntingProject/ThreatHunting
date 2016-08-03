# Finding Web Shells

**Purpose**

Identify web shells (stand-alone|injected)

**Data Required**

Web server logs (apache, IIS, etc.)

**Collection Considerations**

Collect from all webservers, and ensure that parameters are collected.  
POST data should be collected.  

* For apache consider using `mod_security` or `mod_dumpio`
* For IIS use [Failed Request Tracing / Custom Logging](http://serverfault.com/a/90965)

**Analysis Techniques**: 

Stack counting  
String matching

**Description**

* Stack by page hits -- pages with few hits are a typical sign
    * Add more fidelity by combining views from below (none if the above is giving higher fidelity, one, two or all):
        * No referer from client
        * Stack by unique visits per IP -- most only visit the webshell (no other page hits, no js, no images, etc.)
            * this isn't true of injected webshells (where they are injected into an existing page)
        * Stack by UA uniqueness.  This is not always rock solid, but good, because many webshells have client software that sets the UA and many don't change the default
* Look for parameters passed to image files (e.g., `/bad.png?zz=ls`)
* More specific to inject webshells that inject into an existing page:
    * Stack by parameter counts per page -- webshells that create new params on an existing page 
        * Again, you can look if referer is missing, UA uniqueness

**Other Notes**  
Endpoint detection strategies:
* Look for creation of processes whose parent is the webserver (e.g., apache, w3wp.exe); these will come from functions like:
    * PHP functions like `exec()`, `shell_exec()`, etc.
    * asp(.net) functions like `eval()`, `bind()`, etc.)
* Looking for file additions or file changes (if you have a change management process and schedule to easily differentiate 'known good') -- (using something like inotify on linux (or FileSystemWatcher in .NET), to monitor the webroot folder(s) recursively)


There are a few webshell hunt techniques located in other hunts:

* [Finding Known-Bad in Antivirus Logs](https://github.com/DavidJBianco/ThreatHunting/blob/master/hunts/antivirus_logs.md)
* [Suspicious Process Creation via Windows Event Logs](https://github.com/DavidJBianco/ThreatHunting/blob/master/hunts/suspicious_process_creation_via_windows_event_logs.md)

It's important to realize that injected webshells may not be written to disk (e.g., SSJI, XSS, etc.)

**More Info**

None
