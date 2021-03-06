---
layout: page
title: "Q133430: CONN: Macintosh Desktop Database and Mail Performance"
permalink: /kb/133/Q133430/
---

## Q133430: CONN: Macintosh Desktop Database and Mail Performance

{% raw %}

	Article: Q133430
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): 1.0,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Connection Gateway, version 1.0 
	- Microsoft Mail Connection for PC and AppleTalk Networks, version 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run version 1.x of the Microsoft Mail Connection Gateway or version
	3.2x of Microsoft Mail Connection for PC and AppleTalk Networks, performance may
	degrade over time and usage.
	
	NOTE: Microsoft Mail Connection Gateway and Microsoft Mail Connection for PC and
	AppleTalk Networks are the same product; the same changed when it was updated
	from version 1.0 to version 3.2.
	
	CAUSE
	=====
	
	One possible cause is that the Macintosh's desktop file contains invalid
	information.
	
	RESOLUTION
	==========
	
	To resolve, the desktop file can easily be rebuilt with no risk to the Macintosh
	or mail components.
	
	To rebuild the Macintosh desktop
	--------------------------------
	
	1. Hold down the COMMAND and OPTION keys and re-start the Macintosh.
	
	2. Continue to hold down COMMAND+OPTION until the "Would You Like to Rebuild the
	  Desktop..." message appears.
	
	3. Release the COMMAND+OPTION keys and click OK. The rebuild process will begin
	  and end automatically.
	
	  NOTE: Comments manually entered in the Get Info dialog box from the File menu
	  will be discarded in the process.
	
	MORE INFORMATION
	================
	
	The Macintosh desktop is a hidden database file that contains information about
	files, folders, and resources stored on the local drive. When the information in
	the database becomes outdated and/or invalid, system processing may become
	noticeably slower.
	
	Novell NetWare for Macintosh
	----------------------------
	
	In the Novell NetWare environments, there is a separate Macintosh desktop
	database that resides on the NetWare server itself. This hidden database
	contains essentially the same information as the Macintosh database. However, it
	only pertains to NetWare-to-Macintosh shared files.
	
	If the information becomes invalid or corrupt, Macintosh clients may experience
	slow performance when they access a NetWare volume. You should try to rebuild
	the Macintosh desktop database before you try the procedure explained below, as
	it is more intensive and will disconnect the Macintosh NetWare clients
	temporarily from the Novell server.
	
	NOTE: The NetWare Macintosh volume rebuild should take place when the Macintosh
	clients are not logged on to the server and accessing files. The IBM-compatible
	(PC) network clients will not be affected by this procedure.
	
	To rebuild the NetWare Macintosh desktop database
	-------------------------------------------------
	
	1. Unload AFP.NLM at the NetWare server console by typing the following:
	
	  " UNLOAD AFP" (without the quotation marks)
	
	2. Reload AFP.NLM at the NetWare server console by typing the following:
	
	  " LOAD AFP CDT" (without the quotation marks)
	
	  The CDT option clears the existing Desktop database files and installs new
	  database files.
	
	3. To rebuild the information on the new desktop files, go to any Macintosh
	  workstation running System 6.x Finder (not MultiFinder).
	
	  NOTE: System 7.x will not work for this procedure.
	
	4. Open Chooser, and select the NetWare server. Logon as SUPERVISOR, and select
	  which volume(s) to rebuild.
	
	5. As the NetWare server volume(s) mount to the desktop, hold down the
	  COMMAND+OPTION keys until prompted to confirm to rebuild the desktop.
	
	Depending on the size of the Macintosh volume(s), the rebuild may take several
	minutes. After the rebuild has completed, all Macintosh NetWare clients can
	re-attach to the NetWare server.
	
	For more information on NetWare Macintosh database files, see the documentation
	included with the Novell NetWare for Macintosh product.
	
	Additional query words: 1.00 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword2 kbMailSearch kbZNotKeyword3 kbMailConn100 kbMailConn320
	Version           : :1.0,3.2
	
	=============================================================================
	

{% endraw %}
