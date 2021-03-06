---
layout: page
title: "Q252644: Printer Error Messages Incorrectly Redirected to Terminal Server"
permalink: /kb/252/Q252644/
---

## Q252644: Printer Error Messages Incorrectly Redirected to Terminal Server

{% raw %}

	Article: Q252644
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP4,4.0 SP5,4.0 SP6
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbprintkbfixlist
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to print from your Windows NT Server version 4.0, Terminal Server
	edition-based client computer to a printer configured locally on the Terminal
	Server (such as LPT1), you may receive the following error message on the
	Terminal Server console (or the client assigned to session zero):
	
	  Error writing to LPT1: for Document <print job name>: The device is not
	  ready.
	  Do you wish to retry or cancel the job
	
	NOTE: The error message must be cleared on the console (or the client assigned to
	session zero) before the spooler will continue printing any queued requests.
	This error message will not occur on the client computer that requested the
	print job.
	
	CAUSE
	=====
	
	This problem can occur if there was an incorrect check to determine which
	Windows-based computer actually has a direct connection to the local printer.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Windows NT 4.0 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date       Time                 Size    File name     Platform
	  -------------------------------------------------------------
	 01/26/2000  12:26a               149,776 Localspl.dll  (x86)
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Windows NT 4.0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg kbprint kbfixlist
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServ400sp4 kbNTTermServ400sp5 kbNTTermServ400sp6 kbNTTermServSearch
	Version           : winnt:4.0,4.0 SP4,4.0 SP5,4.0 SP6
	Hardware          : ALPHA x86
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
