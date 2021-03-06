---
layout: page
title: "Q242123: Macintosh Clients Cannot See Server When PDC is Moved to New Net"
permalink: /kb/242/Q242123/
---

## Q242123: Macintosh Clients Cannot See Server When PDC is Moved to New Net

{% raw %}

	Article: Q242123
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may be unable to see a primary domain controller (PDC) using a Macintosh
	client computer. The zone may be listed on the clients, but the server may not,
	and the server may not have a list of zones.
	
	CAUSE
	=====
	
	This issue can occur if you move a primary domain controller (PDC) that is
	running Services for Macintosh (SFM) from one network port to another on the
	same network segment.
	
	RESOLUTION
	==========
	
	To resolve this issue, remove and reinstall Services for Macintosh on the
	Windows NT Server-based computer, to bind the protocol and generate a list of
	zones. To do this, follow these steps:
	
	1. Remove Services for Macintosh:
	
	  a. In Control Panel, double-click Network, and then click the Services tab.
	
	  b. Click Services for Macintosh, and then click Remove.
	
	  c. Restart the computer.
	
	2. Reinstall Services for Macintosh:
	
	  a. In Control Panel, double-click Network, and then click the Services tab.
	
	  b. In the Network Service list, click Services for Macintosh, and then click
	     Add.
	
	  c. Insert the Microsoft Windows NT Server 4.0 CD-ROM into your CD-ROM drive,
	     and then type the drive letter where the server software is located in the
	     appropriate box.
	
	  d. Click Continue, and then click OK if the Setup Message dialog box appears.
	
	  e. Click Close.
	
	  f. In the Microsoft AppleTalk Protocol Properties dialog box, click the
	     General tab.
	
	  g. In the Default Adapter box, click the default network adapter to run
	     AppleTalk.
	
	NOTE: If you already have a network adapter that provides AppleTalk routing
	information, the Default Zone box will contain zone options. Click the zone
	where you want to use AppleTalk services. An AppleTalk zone is similar to a
	workgroup in Microsoft networks. An AppleTalk zone is where the file server for
	the Macintosh and any Windows NT Server-based printers appear when Macintosh
	users select them from the Chooser.
	
	3. Configure the Windows NT Server-based computer to act as an AppleTalk router:
	
	  a. In the Microsoft AppleTalk Protocol Properties dialog box, click the
	     Routing tab, and then click the Enable Routing check box.
	
	     NOTE: Clicking the Enable Routing check box is useful only if the AppleTalk
	     protocol is bound to more than one network adapter. If Services for
	     Macintosh is installed on only one server, or if no other devices are
	     acting as AppleTalk routers on the network, click the Use this router to
	     seed the network check box.
	
	  b. Click OK.
	
	4. Save all work and quit all programs, and then restart the computer to make
	  the new settings take effect.
	
	Additional query words: AppleTalk protocol zones
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
