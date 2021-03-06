---
layout: page
title: "Q289582: HTTPS Connections Fail After You Upgrade to IIS 4.0 &amp; Enable SSL"
permalink: /kb/289/Q289582/
---

## Q289582: HTTPS Connections Fail After You Upgrade to IIS 4.0 &amp; Enable SSL

{% raw %}

	Article: Q289582
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbDSupport
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After you upgrade from previous versions of Internet Information Server (IIS) to
	the Microsoft Windows NT 4.0 Option Pack (IIS 4.0) and enable Secure Sockets
	Layer (SSL), browsers may fail to connect through HTTPS. The browser may return
	one of the following error messages:
	
	  Page Cannot Be Displayed
	
	  -or-
	
	  Page Cannot Be Found
	
	CAUSE
	=====
	
	This problem occurs when the Filter Dlls registry entry is left with an invalid
	path to the Sspifilt.dll file after you upgrade.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this problem, make sure that Sspifilt.dll is not loaded in the legacy
	W3SVC registry entry as follows:
	
	1. On the Start menu, click Run, and then type "regedt32" (without the quotation
	  marks).
	
	2. In Registry Editor, locate the
	  HKEY_Local_Machine\System\CurrentControlSet\Services\W3SVC\Parameters\Filter
	  Dlls registry key.
	
	3. Double-click Filter Dlls to display the string value.
	
	4. Delete the path entry for Sspifilt.dll (which is
	  <Drive>\WINNT\System32\Inetsrv\Sspifilt.dll by default.)
	
	5. Click OK to close the String Editor.
	
	6. Restart the server for the changes to take effect.
	
	Additional query words: iis iis4 iis3
	
	======================================================================
	Keywords          : kbDSupport 
	Technology        : kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
