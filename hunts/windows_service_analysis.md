#Windows Service Analysis

**Purpose**: Find suspicious Windows services running across a network

**Data Required**: Info about running services on endpoints; For `svchost` services, list of DLLs loaded inside

**Collection Considerations**: May need a host agent (e.g., MS Sysinternals `psservice.exe` and `listdlls.exe`) to collect this regularly.  Some Windows systems log service configuration, start & stop events, which might also be useful.

**Analysis Techniques**: Stack counting

**Description**

An example of the data returned by `psservice.exe` is:

  SERVICE_NAME: ALG  
  DISPLAY_NAME: Applicaton Layer Gateway Service  
  Provides support for 3rd party protocol plug-ins for Internet Connec+on Sharing

     TYPE : 10 WIN32_OWN_PROCESS
     START_TYPE : 3 DEMAND_START
     ERROR_CONTROL : 1 NORMAL
     BINARY_PATH_NAME : C:WINDOWSSystem32alg.exe
     LOAD_ORDER_GROUP :
     TAG :0
     DEPENDENCIES :
     SERVICE_START_NAME: NT AUTHORITYLocalService
     FAIL_RESET_PERIOD : 900 seconds
     FAILURE_ACTIONS : Restart     DELAY: 120000 seconds
         : Restart     DELAY: 300000 seconds
         : None        DELAY: 0 seconds

An example of _listdlls_ output is:

	svchost.exe pid: 620
	Com		mand line: C:WindowsSystem32svchost.exe -k WerSvcGroup
	Base       Size      Path
	0x70eb0000 0x1e000   c:windowssystem32wersvc.dll
	Verified: Invalid Signature
	Publisher: n/a  
	Description: n/a  
	Product: n/a Version: n/a File version: n/a

Look for 

* Rare `SERVICE_NAME` or `DISPLAY_NAME` values
    * GUID service names
    * Random service names
* Blank fields which normally hold values
* Unusual directories in the `BINARY_PATH_NAME`

For `svchost` services, list all DLLs loaded inside them (using `listdlls`) and look for:

* Rare DLLs and/or locations
* Unsigned DLLs or those with invalid signatures

**More Info**

* [Intrusion Hunting for the Masses](https://www.youtube.com/watch?v=YLgycMCPo4c), David Sharpe (HackMiami 2016)



