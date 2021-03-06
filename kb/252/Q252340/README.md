---
layout: page
title: "Q252340: How to Create and Start a Service on a Remote Computer"
permalink: /kb/252/Q252340/
---

## Q252340: How to Create and Start a Service on a Remote Computer

{% raw %}

	Article: Q252340
	Product(s): Microsoft Windows NT
	Version(s): 2000,3.51 (all service packs),4.0,4.0 SP4,4.0 SP5
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51 (all service packs), 4.0 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4, 4.0 SP5, Terminal Server Edition 
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to create and start a service remotely on a Windows
	NT-based or Windows 2000-based computer from the command line.
	
	In this scenario, the program file resides on all the remote computers; you want
	to write a script to create and start the service automatically.
	
	MORE INFORMATION
	================
	
	The Netsvc.exe and Instsrv.exe tools from the Resource Kit do not create a
	service on a remote computer. The Srvinstw.exe tool from the Resource Kit is a
	program that you use to create remote services, but it is not a command-line
	tool that you can use in a script.
	
	To create a script to create and start a service on a remote computer, use the
	Sc.exe tool from the Resource Kit. The syntax for this utility is:
	
	  sc \\<computername> create notepad binpath=
	  c:\winnt\system32\notepad.exe type= own start= auto depend= "+TDI Netbios"
	
	This particular command instructs the remote computer to create the "Notepad"
	service, then tells the computer where it can find the program file for this
	service.
	
	The start=auto option instructs the computer to start the new Notepad service
	automatically when the computer is booted. The depend="+TDI Netbios" option
	tells the computer that it is dependent on the TDI group and on the NetBIOS
	service. Note that you must add quotation marks around the list of
	space-separated dependencies.
	
	For more detailed information about the Sc.exe tool, please see the Sc-dev.txt
	file located in the Resource Kit.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbNTTermServ400 kbNTTermServ400sp4 kbNTTermServ400sp5 kbNTTermServSearch kbWinAdvServSearch
	Version           : :2000,3.51 (all service packs),4.0,4.0 SP4,4.0 SP5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
