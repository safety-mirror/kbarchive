---
layout: page
title: "Q89171: Using the Invisible Network with Windows"
permalink: /kb/089/Q89171/
---

## Q89171: Using the Invisible Network with Windows

{% raw %}

	Article: Q89171
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information on Invisible Software's product Invisible
	Network and its use with Microsoft Windows 3.0 and 3.1. The following topics are
	included:
	
	- Using Invisible Network with Windows 3.0
	
	- Using Invisible Network with Windows 3.1
	
	MORE INFORMATION
	================
	
	Using Invisible Network with Windows 3.0
	----------------------------------------
	
	Invisible Network provides nondedicated MS-DOS server operation in a peer-to-peer
	environment. It will only function with Invisible Software's proprietary
	Ethernet or twisted pair network adapters.
	
	Setup
	-----
	
	Invisible Network 2.21a or later should be used. It will be detected by Windows
	3.0 as "IBM PC LAN," provided that the network was loaded before the Windows
	Setup program is run, and that the /I parameter (used to disable Windows
	automatic hardware detection) is not being used. This is the correct choice for
	this network.
	
	Printing
	--------
	
	Printing over the network to a shared printer should work correctly using LPT1:,
	LPT2:, or LPT3:. It has been noted, however, that the Windows Print Manager
	displays the message
	
	  A general network error has occurred.
	
	In addition,
	
	  [NETWORK ERROR]
	
	is displayed on the status line for the redirected printer. For this reason, it
	is recommended that you disable the use of the Print Manager by choosing the
	Printers icon from the Control Panel and clearing the Use Print Manager check
	box.
	
	WARNING: If a job is printed while the Print Manager is in a restored state (not
	minimized), the workstation hangs. This is an additional reason to disable the
	Print Manager. Invisible Software is researching this problem.
	
	386 Enhanced Mode
	-----------------
	
	386 enhanced mode is not recommended at this time on any machine that is
	designated as a server (that is, any machine that shares a printer and/or disk
	service). Workstations can run 386 enhanced mode.
	
	Invisible Software recommends adding the following entries to the [386enh]
	section of the Windows SYSTEM.INI file on workstations running in 386 enhanced
	mode:
	
	     network=*vnetbios,*dosnet
	     FileSysChange=off
	     InDOSPolling=TRUE
	     INT28Critical=TRUE
	     ReflectDosInt2A=FALSE
	     UniqueDOSPSP=FALSE
	     LPT1AutoAssign=0
	     LPT2AutoAssign=0
	     LPT3AutoAssign=0
	     PerVMFiles=0
	
	Additionally, you may need to add the line
	
	     EMMExclude=XXXX-YYYY
	
	where XXXX is the beginning address and YYYY is the ending address of the network
	adapter in the reserved memory area.
	
	Using Invisible Network with Windows 3.1
	----------------------------------------
	
	To run the Invisible Network with Windows 3.1, you must use version 3.13.
	
	Steps to Install Invisible Network into Windows 3.1
	---------------------------------------------------
	
	1. Run Windows 3.1.
	
	2. From the File menu, choose Run.
	
	3. Type "setup" (without the quotation marks) and press ENTER.
	
	4. From the Options menu, choose Change System Settings.
	
	5. From the Network list box, choose Other Network.
	
	6. When asked to insert the network driver disk, supply the following path:
	
	  C:\NET30
	
	The Invisible Network software loads. You will have to exit and restart Windows.
	
	Invisible Network is manufactured by Invisible Software, a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding this product's
	performance or reliability.
	
	Additional query words: 3.00 3.00a 3.10 3.11 3rdparty net30 net-30 invisable invisiable
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
