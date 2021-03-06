---
layout: page
title: "Q262223: Delprof Does Not Delete Profiles When Run by Schedule Service"
permalink: /kb/262/Q262223/
---

## Q262223: Delprof Does Not Delete Profiles When Run by Schedule Service

{% raw %}

	Article: Q262223
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0; :4.0
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may experience problems when you schedule the Delprof.exe utility to run by
	using the AT command (also known as the Schedule service). When you do so, the
	targeted profile folders are not deleted from the %SystemRoot%\Profiles folder.
	However, users with existing profiles are logged on with a new default profile,
	or a new copy of their roaming profile with a <Username>.00<x> file
	name.
	
	CAUSE
	=====
	
	By default, the Schedule service runs under the Local System account. The Local
	System account does not have network privileges. Delprof cannot perform its
	tasks correctly when it is running under the Local System account.
	
	RESOLUTION
	==========
	
	Reconfigure the Schedule service to run under a user account with administrator
	privileges on the local computer.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	This is actually a limitation of the Local System account. Because Delprof.exe
	is network-aware, it is designed to make a network connection to the computer on
	which it is deleting profiles, even if that is the local computer. It does so by
	making a connection to the Admin$ share on the computer. The Local System
	account has no permissions to access the computer by using this method.
	
	However, the second function of Delprof.exe is to delete the appropriate user's
	entry in the registry at:
	
	  Hkey_Local_Machine\Software\Microsoft\WindowsNT\CurrentVersion\ProfileList
	
	This second function does not require a network connection when it is run on the
	local computer, and succeeds. The files for the profile are left on the server,
	but the pointer needed to link the user to the profile is deleted. Therefore,
	the user receives a new profile.
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q158825 System and User Account Difference with AT Command
	
	  Q124184 Service Running as System Account Fails Accessing Network
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0; :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
