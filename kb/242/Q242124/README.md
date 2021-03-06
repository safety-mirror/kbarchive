---
layout: page
title: "Q242124: Err Msg: No End Points Available from End Point Mapper"
permalink: /kb/242/Q242124/
---

## Q242124: Err Msg: No End Points Available from End Point Mapper

{% raw %}

	Article: Q242124
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you install a clean Domain Name Server (DNS) database, remove and reinstall
	the DNS service in Microsoft Windows NT Server 4.0, and create new zones, you
	may receive the following error message:
	
	  No end points available from end point mapper.
	
	CAUSE
	=====
	
	This behavior can occur if the DNS service is not completely removed.
	
	RESOLUTION
	==========
	
	IMPORTANT: This article contains information about modifying the registry.
	Before you modify the registry, make sure to back it up and make sure that you
	understand how to restore the registry if a problem occurs. For information
	about how to back up, restore, and edit the registry, click the following
	article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this issue, completely remove and reinstall the DNS service, and then
	restore or create zones:
	
	1. Copy the DNS zone files from the \Winnt\System32\Dns folder to another
	  folder.
	
	2. Remove the DNS service:
	
	  a. In Control Panel, double-click Network.
	
	  b. Click the Services tab.
	
	  c. Click Microsoft DNS Server, and then click Remove.
	
	  d. Click Yes when you are prompted to confirm the removal of DNS.
	
	  e. Click Close.
	
	  f. When you are prompted to restart the computer, click No.
	
	3. Remove the DNS registry keys:
	
	  a. Start Registry Editor.
	
	  b. Under HKEY_LOCAL_MACHINE, delete the following registry keys:
	
	 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DNS
	 HKEY_LOCAL_MACHINE\Software\Microsoft\DNS
	 HKEY_LOCAL_MACHINE\Software\Microsoft\DNS Administrator
	
	  c. Under HKEY_CURRENT_USER, delete the following registry key:
	
	 HKEY_CURRENT_USER\Software\Microsoft\DNS Administrator
	
	4. Quit Registry Editor.
	
	5. Restart the computer.
	
	6. Reinstall the DNS service:
	
	  a. In Control Panel, double-click Network.
	
	  b. Click the Services tab, and then click Add.
	
	  c. Click Microsoft DNS Service, and then click OK.
	
	  d. Click Close.
	
	IMPORTANT: Do not restart the computer after you reinstall the DNS service.
	
	7. Reinstall the latest Windows NT 4.0 service pack.
	
	8. Restart the computer.
	
	9. If applicable, update Routing and Remote Access Server, and then reapply any
	  hotfixes that you have added to this computer.
	
	10. Restore the DNS zone files to their original folder, or create fresh DNS
	  zones.
	
	MORE INFORMATION
	================
	
	If you unbind the Windows Internet Name Service (WINS) Client (TCP/IP) protocol
	from the network adapter, DNS does not function properly. For more information
	about DNS and WINS, see the following article in the Microsoft Knowledge Base:
	
	  Q183901 Microsoft DNS Server Depends on the WINS Client Binding
	
	Additional query words: nt 4.0 error endpoint create
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
