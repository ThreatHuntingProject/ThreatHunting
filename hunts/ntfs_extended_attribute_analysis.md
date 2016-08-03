#NTFS Extended Attribute Analysis

**Purpose**: Identify data hiding in extended attributes on files in an NTFS filesystem, which are otherwise rarely used.  

**Data Required**: NTFS Master File Table (MFT) data from a single host

**Collection Considerations**: Run `fget.exe` on each NTFS filesystem on a host to capture the raw data, then parse into records and fields with something like `analyzeMFT.py`

**Analysis Techniques**: Stack counting

**Description**

The MFT holds detailed metadata about files and directories on a file system.  There are many different attributes that are technically possible to attach to files and dirs, but in practice are never used.  The so-called "Extended Attributes" section is thought to be present for OS/2 compatibility, but no one ever used OS/2, so anything in the EA is pretty suspicious.  

Stack the data by full path and filename, "EA" an "EA Information" fields.  Look for:

* Rare values in the MFT "EA" or "EA Information" fields.  There may be some legitimate use of these in your environment, but hopefully these uses will have a high count.
    * Anything in `/Windows/winsxs` or `/Windows/CSC` is probably legit


**Other Notes**

**More Info**

- [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)
- [Extracting ZeroAccess from NTFS Extended Attributes](http://journeyintoir.blogspot.com/2012/12/extracting-zeroaccess-from-ntfs.html), Corey Harrell
- [Various articles on HMFT](http://www.hexacorn.com/blog/category/software-releases/hmft/), Hexacorn, Ltd.

