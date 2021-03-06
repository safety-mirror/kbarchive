---
layout: page
title: "Q217069: Serial Printer Communication Fault Pop-up Notification Available"
permalink: /kb/217/Q217069/
---

## Q217069: Serial Printer Communication Fault Pop-up Notification Available

{% raw %}

	Article: Q217069
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP4
	Operating System(s): 
	Keyword(s): kbWinNT400sp5fix
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4 
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When serially connected printers experience a communication break or an out of
	resource condition such as out of paper on Windows NT 4.0, this is not
	communicated back to the server through a dialog box or a pop-up message. It
	simply stops printing to the printer, and continues spooling the print job in
	the spooler until it is finished being sent from the client. The print job will
	now sit in the spooler until someone resolves the communication or resource
	problem. If the print job is restarted before the printer problem is resolved,
	it is possible for the spooler to think the printer problem is resolved and send
	the spooled up print job to the bit bucket.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	the individual software update. For information on obtaining the latest service
	pack, please go to:
	
	- http://www.microsoft.com/Windows/ServicePacks/
	
	-or-
	
	- Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For information on obtaining the individual software update, contact Microsoft
	Product Support Services. For a complete list of Microsoft Product Support
	Services phone numbers and information on support costs, please go to the
	following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0. This problem was
	first corrected in Windows NT version 4.0 Service Pack 5.
	
	MORE INFORMATION
	================
	
	The updated code now creates a pop-up message when a communication error occurs.
	The user can respond to the fault when it has been resolved. If the fault is
	resolved but you cannot get to the server to respond, the system will
	automatically retry approximately every 5 seconds, and, if successful, will
	remove the pop-up message.
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          : kbWinNT400sp5fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTW400sp4 kbWinNTSsearch kbWinNTS400sp4 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0,4.0 SP4
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
