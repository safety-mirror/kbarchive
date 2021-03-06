---
layout: page
title: "Q174257: XCON: Eicon Default Setting Only Allows Four MTA Associations"
permalink: /kb/174/Q174257/
---

## Q174257: XCON: Eicon Default Setting Only Allows Four MTA Associations

{% raw %}

	Article: Q174257
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	
	IMPORTANT: This article contains information about editing the registry. Before
	you edit the registry, make sure you understand how to restore it if a problem
	occurs. For information about how to do this, view the "Restoring the Registry"
	Help topic in Regedit.exe or the "Restoring a Registry Key" Help topic in
	Regedt32.exe.
	
	When you use the Microsoft Exchange X.400 connector over an X.25 card to connect
	to another system, you may receive the following error messages when you try to
	open an association to another system:
	
	  Event ID: 9102
	  Source: MSExchangeMTA
	  Type: Warning
	  Category: Resource
	
	  An X.25 resource limit was reached while attempting to open an association.
	  Connection control block: 3. Logical session number: 0. Error code: 9. [BASE
	  IL EICON RESULT 16 144] (10)
	
	  Event ID: 9131
	  Source: MSExchangeMTA
	  Type: Information
	  Category: Field Engineering
	
	  An X.25 connection ended normally (hung up). Connection control block:
	  3.. Logical session number: 0. Return code: 265. [BASE IL EICON WORKER 15
	  210](10)
	
	  Event ID: 9134
	  Source: MSExchangeMTA
	  Type: Information
	  Category: Field Engineering
	
	  An X.25 call on was made for address
	  333130343030303837320000000000000000000000000000000000000000000000000000
	  000000000000000000000000000000000000000000 on port 1. Connection control
	  block: 3. Logical session number: 0. Return code: 0. [BASE IL EICON WORKER 15
	  210] (10)
	
	CAUSE
	=====
	
	This problem usually occurs when associations over the X.25 WAN adapter are
	already open, and the card is simply busy. By default, the Exchange message
	transfer agent (MTA) attempts to use up to 20 X.25 two-way virtual circuits.
	With the Eicon WAN adapter, the WAN Services for Windows NT software sets the
	default two-way virtual circuits to four. Therefore, when the MTA makes four
	associations the card will no longer accept open associations.
	
	RESOLUTION
	==========
	
	To prevent the MTA from attempting to open an association over a busy X.25 card,
	use of the following two methods:
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	1. Change the default two-way virtual circuits value for the MTA from 20 to 4 to
	  reflect the default setting of the Eicon WAN adapter. To do this, edit the
	  Windows NT registry and make the following adjustment:
	
	     HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeMTA
	     \Parameters
	     Eicon X.25 Connections
	
	  Change the default two-way virtual circuits value for the MTA to match the
	  Eicon default of 4 or whatever the Eicon two-way virtual circuits value is
	  set to.
	
	-OR-
	
	2. Use the WAN Services for Windows NT to change the WAN adapter to 20 to match
	  the MTA default value.
	
	Additional query words: eicon atlantis mci sprint att x25 wan services
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
