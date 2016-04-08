#Shimcache/Amcache

**Purpose**: Identify potential malware by finding "rare" binaries executed across endpoints.

**Data Required**: Windows Shimcache or Amcache entries

**Collection Considerations**: These are cache entries, not logs, so need to be collected directly from each endpoint, usually by an agent.

**Analysis Techniques**: Stack counting

**Description**

Shimcache/Amcache records basic info about the last several (max 1024) executables that ran.  If you collect this list frequently, you can use it to build a list of executable filenames and locations that run on each system.  Shimcache is the older implementation.  Starting with Windows 8 and Server 2012, it was replaced by Amcache.  The format is very different, since Amcache has lots more info it can provide, but the intent is the same.

Stack count the filenames and/or directory paths to find rare files executed, rare locations from which files are executed.  Assume rare files are more suspicious and investigate accordingly.

**More info**

- [https://www.fireeye.com/blog/threat-research/2015/06/caching_out_the_val.html]()
- [https://dl.mandiant.com/EE/library/Whitepaper_ShimCacheParser.pdf]()
- [https://github.com/mandiant/ShimCacheParser]()
- [https://www.fireeye.com/blog/threat-research/2012/04/leveraging-application-compatibility-cache-forensic.html]()
- [https://github.com/williballenthin/python-registry/blob/master/samples/amcache.py]()
- [https://gist.github.com/williballenthin/ee512eacb672320f2df5#file-amcache_py_examples-md]()
- [http://www.swiwforensics.com/2013/12/amcachehve-in-windows-8-goldmine-for.html]()
- [http://www.swiwforensics.com/2013/12/amcachehve-part-2.html]()
- Intrusion Hunting for the Masses - David Sharpe (DerbyCon 2015)
- [https://www.fireeye.com/blog/threat-research/2015/10/shim_shady_live_inv.html]()