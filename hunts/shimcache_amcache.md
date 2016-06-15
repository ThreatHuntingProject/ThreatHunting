#Shimcache/Amcache

**Purpose**: Identify potential malware by finding "rare" binaries executed across endpoints.

**Data Required**: Windows Shimcache or Amcache entries

**Collection Considerations**: These are cache entries, not logs, so need to be collected directly from each endpoint, usually by an agent.

**Analysis Techniques**: Stack counting

**Description**

Shimcache/Amcache records basic info about the last several (max 1024) executables that ran.  If you collect this list frequently, you can use it to build a list of executable filenames and locations that run on each system.  Shimcache is the older implementation.  Starting with Windows 8 and Server 2012, it was replaced by Amcache.  The format is very different, since Amcache has lots more info it can provide, but the intent is the same.

Stack count the filenames and/or directory paths to find rare files executed, rare locations from which files are executed.  Assume rare files are more suspicious and investigate accordingly.

**More info**

- [Caching Out: The Value of Shimcache for Investigators](https://www.fireeye.com/blog/threat-research/2015/06/caching_out_the_val.html), FireEye
- [Leveraging the Application Compatibility Cache in Forensic Investigations](https://dl.mandiant.com/EE/library/Whitepaper_ShimCacheParser.pdf), Mandiant
- [ShimCacheParser](https://github.com/mandiant/ShimCacheParser), Mandiant
- [amcache.py](https://gist.github.com/williballenthin/ee512eacb672320f2df5#file-amcache_py_examples-md), Will Ballenthin
- [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)
- [ShimShady: Live Investigations of the Application Compatibility Cache](https://www.fireeye.com/blog/threat-research/2015/10/shim_shady_live_inv.html), Fred House, Claudiu Teodorescu, Andrew Davis (FireEye)