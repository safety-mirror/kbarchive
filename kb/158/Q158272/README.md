---
layout: page
title: "Q158272: Printer Disappears After Upgrading to Windows NT 4.0"
permalink: /kb/158/Q158272/
---

## Q158272: Printer Disappears After Upgrading to Windows NT 4.0

{% raw %}

	Article: Q158272
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbprint
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you upgrade from Windows NT 3.51 to Windows NT 4.0, your printer may no
	longer exist.
	
	CAUSE
	=====
	
	When you upgrade, the printer is not re-created if Setup cannot locate a
	suitable printer driver with which to upgrade the current printer driver. This
	behavior can occur if you are using a third-party printer driver or if the
	Windows NT 3.51 printer driver name does not match the Windows NT 4.0 printer
	driver name.
	
	RESOLUTION
	==========
	
	To prevent the Windows NT printer from being deleted during the upgrade, change
	the Windows NT 3.51 printer to use a driver that Windows NT 4.0 supports. In
	Windows NT 3.51 Print Manager, select the Properties of the printer and then
	select a printer driver that is supported in Windows NT 4.0.
	
	MORE INFORMATION
	================
	
	The printer driver name mismatch is usually caused by the use of a driver
	supplied by the printer manufacturer.
	
	
	Additional query words: print queue
	
	======================================================================
	Keywords          : kbprint 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
