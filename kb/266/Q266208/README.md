---
layout: page
title: "Q266208: RPC, Protected Storage Services May Not Start on Workstation wit"
permalink: /kb/266/Q266208/
---

## Q266208: RPC, Protected Storage Services May Not Start on Workstation wit

{% raw %}

	Article: Q266208
	Product(s): Microsoft Exchange
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- the operating system: Microsoft Windows NT 4.0 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using the Novell IntranetWare client version 4.50 or later on a
	computer running Microsoft Windows NT Workstation 4.0, the protected storage
	service that depends on remote procedure call (RPC) service may not start and
	you may receive the following event log notices:
	
	  Event ID: 7022
	  Source: Service Control Manager
	  Type: Error
	  Description: The remote procedure call (RPC) service hung on startup.
	
	  Event ID: 7001
	  Source: Service Control Manager
	  Type: Error
	  Description: HTTP server service depends on the MUP service which failed to
	  start because of the following error: An instance of the service is already
	  running.
	
	RESOLUTION
	==========
	
	To resolve this behavior, remove the IntranetWare client and then restart the
	computer.
	
	MORE INFORMATION
	================
	
	For additional information about how to remove a Novell client, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q175806 How to Remove IntranetWare Client for Windows NT
	
	For more information about how to remove specific versions of the Novell client,
	refer to the product manual or visit the Novell Web site at
	http://www.novell.com.
	
	This behavior may also occur on some Compaq computers. Apply the latest Compaq NT
	Support Software Disk (NT SSD) from the Compaq Smartstart CD-ROM. Then manually
	stop all the services and re-add them one at a time to identify which device is
	causing the behavior.
	
	For information about how to contact Compaq Computer Corporation, click the
	appropriate article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOSWinSearch kbOSWinNT400 kbOSWinNTSearch
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
