---
layout: page
title: "Q278954: XADM: Recurring Appts Made by CDO Not Added to Local F/B Map"
permalink: /kb/278/Q278954/
---

## Q278954: XADM: Recurring Appts Made by CDO Not Added to Local F/B Map

{% raw %}

	Article: Q278954
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Operating System(s): 
	Keyword(s): exc55 exc55sp1 exc55sp2 exc55sp3 kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3, 5.5 SP4 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Recurring appointments that are created by Collaboration Data Objects (CDO) such
	as Outlook Web Access or AutoAccept Script through Events Service in Exchange
	Server, may not be reflected in the local or public free-and-busy map for the
	mailbox.
	
	CAUSE
	=====
	
	In some cases, the recurring appointment data that is held in binary form on a
	mailbox's calendar may exceed more than one binary record. If the data exceeds
	more than one record, the appointment Entry ID (EID) is needed to link the
	multiple records together. The process by which CDO extracts the appointments
	and necessary MAPI properties to build the local and public free-and-busy map
	does not include the EID of appointments. The failure to extract this EID
	property cause CDO to be unable to retrieve these particular appointments into
	its result set. This, in turn, causes the free-and-busy data for these
	particular appointments to not get propagated out to the local or public
	free-and-busy maps.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server version 5.5 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: CDO
	
	+-------------------------+
	| File name | Version     | 
	+-------------------------+
	| Cdo.dll   | 5.5.2654.24 | 
	+-------------------------+
	
	
	
	For additional information on how to download the update for this problem, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q289606 XGEN: Exchange Server 5.5 Post-Service Pack 4 Collaboration Data
	  Objects Fixes Available
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	The CDO process for propagating the free-and-busy data from a mailbox calendar
	to the Free/Busy public folder for a given site is as follows:
	
	- A change is made to a mailbox calendar item.
	
	- After the change is made, the mailbox-wide MAPI property that holds the
	  free-and-busy data is deleted in its entirety.
	
	- CDO queries an already established table of appointments to get a list from
	  which to regenerate the free-and-busy data for the mailbox.
	
	- This CDO list is taken from the first day of the current month and spans one
	  year from that day. That is, if a change is made on November 8, 2000, the
	  free-and-busy data is regenerated between the dates November 1, 2000, and
	  November 1, 2001.
	
	- Free-and-busy data is then extracted from this CDO list, and the mailbox-wide
	  MAPI property is rebuilt to include this new data.
	
	- From this new data in the local free-and-busy map, a message is queued up to
	  be sent to the site's Free/Busy public folder.
	
	It is important to understand the process when you are troubleshooting
	free-and-busy problems. You must understand that the public free-and-busy data
	is populated by what is in the mailbox's local free-and-busy map. So, if
	inconsistencies are seen between a mailbox's calendar and the public
	free-and-busy data, investigate the local free-and-busy data first. If the local
	free-and-busy data is not synchronized with the mailbox's calendar, the public
	free-and-busy data will not be correct.
	
	
	Additional query words: fbutil exe
	
	======================================================================
	Keywords          : exc55 exc55sp1 exc55sp2 exc55sp3 kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3 kbExchange550SP4
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
