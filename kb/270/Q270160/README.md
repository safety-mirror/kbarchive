---
layout: page
title: "Q270160: XADM: Unable to View Free/Busy Information Across Exchange Sites"
permalink: /kb/270/Q270160/
---

## Q270160: XADM: Unable to View Free/Busy Information Across Exchange Sites

{% raw %}

	Article: Q270160
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you try to view free-and-busy information for users in another site, when
	you click the Attendee Availability tab, only a string of hash marks (/) are
	displayed for those users, for example:
	
	  <Username> \\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
	
	You may also experience the following symptoms:
	
	- Directory replication issues
	
	- Issues sending or receiving e-mail messages
	
	- Public folder replication issues
	
	CAUSE
	=====
	
	This issue can occur if you have an anti-virus software package installed that
	is being used in virus scan Application Programming Interface (API) mode.
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To work around this issue, make sure that the BackgroundScanning value is enabled
	and increase the OpenRetryDelay value from the default setting.
	
	NOTE: These procedures reduce but may not eliminate the number of error messages
	that are displayed during MAPI operations.
	
	To enable the BackgroundScanning value:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the BackgroundScanning value under the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS\VirusScan
	
	3. If the value is set to 0, change the value to 1. To do so, click Binary on
	  the Edit menu, type "1" (without the quotation marks), and then click OK.
	
	4. Quit Registry Editor.
	
	The Background Scanning process begins one minute after you change this key.
	After you enable the BackgroundScanning value, Microsoft recommends that you
	allow approximately one hour to pass for each gigabyte (GB) of attachments that
	are stored in your private information store before you perform a MAPI operation
	to ensure that all attachments have been scanned. After that amount of time,
	MAPI error messages are greatly reduced or may be eliminated.
	
	To increase the OpenRetryDelay value:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the OpenRetryDelay value under the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS\VirusScan
	
	3. On the Edit menu, click DWORD, type "5000" (without the quotation marks), and
	  then click OK.
	
	4. Quit Registry Editor.
	
	If the OpenRetryDelay value does not exist, you must create it. To do so:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS\VirusScan
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value Name: OpenRetryDelay
	  Data Type: REG_DWORD
	  Radix: Decimal
	  Value: 5000
	
	4. Quit Registry Editor.
	
	MORE INFORMATION
	================
	
	Attachments are scanned when they are sent or received by the Exchange Server
	computer if the anti-virus API is enabled. However, you need to rescan those
	attachments that are already present when an operation gains access to those
	attachments when you install the anti-virus software or update the virus
	signature file, unless the Background Scanning process has scanned those
	attachments. This procedure ensures that those attachments have been checked
	with the latest virus signature file. The Background Scanning process begins a
	full scan of all attachments in the information store if the virus signatures
	change or the vendor of the virus software changes.
	
	The BackgroundScanning value is disabled by default on many types of third-party
	anti-virus software. In addition, the OpenRetryDelay value that the anti-virus
	software uses determines the time interval (in milliseconds) that the
	information store pauses before the information store attempts to reopen
	attachments that are being scanned when the client requests them. If the
	attachment is not scanned and made available to the MAPI request within this
	time interval, a timeout error message is displayed. By default, the information
	store uses a setting of 500 milliseconds (msec), or one-half of a second, unless
	otherwise specified in the registry.
	
	Because all attachments are rescanned after virus signatures are updated before
	an operation can gain access to those attachments, it is important that you plan
	for signature update to occur during off-peak hours if possible. When you
	schedule the update for off-peak hours, you allow time for the attachments to be
	scanned and made available to any MAPI operations.
	
	
	Additional query words: vapi
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
