---
layout: page
title: "Q248191: SCSI Time-Out Error Messages with EMC Symmetrix Disk Arrays"
permalink: /kb/248/Q248191/
---

## Q248191: SCSI Time-Out Error Messages with EMC Symmetrix Disk Arrays

{% raw %}

	Article: Q248191
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP4
	Operating System(s): 
	Keyword(s): kb3rdparty kbenv kberrmsg kbnetwork
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If you use Windows NT 4.0-based servers using EMC Symmetrix disk arrays, you may
	log SCSI time-out errors during the online upgrades and reconfiguration
	operations.
	
	  Event Viewer Example:
	  Event ID: 9
	  Source: EMC_Driver_name
	  Description: The device, \Device\ScsiPort0, did not respond within the timeout
	  period.
	
	CAUSE
	=====
	
	EMC's Symmetrix disk array supports on line upgrade and reconfiguration
	operations that require stalling I/O operations at certain points during the
	operation. If these operations are carried out while the Symmetrix array is
	under load, the I/O stall may last longer than the default 10 second time-out
	value that Windows NT 4.0 sets for SCSI operations.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To resolve this issue, add the TimeOutValue DWORD value in the following registry
	key. EMC recommends setting the value data to 60 seconds in decimal format.
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Disk\
	
	This procedure is described in the Windows NT 4.0 DDK documentation release
	notes.
	
	EMC's Hardware Compatibility testing for HCL certification is done with
	TimeOutValue set to 60 seconds.
	
	MORE INFORMATION
	================
	
	Most computers do not need this registry value. If you have a mass storage
	device that is continually timing out on complex operations, you can use this
	registry value to set the time-out period to a slightly higher value. Make sure
	that the programs you use do not have time out logic, which might cause a
	problem if this value is reset. Consult your ISV or program provider before you
	change the SCSI timeout parameters.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words:
	
	======================================================================
	Keywords          : kb3rdparty kbenv kberrmsg kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400sp4 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0,4.0 SP4
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
