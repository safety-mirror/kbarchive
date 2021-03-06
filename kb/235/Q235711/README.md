---
layout: page
title: "Q235711: Fatal Exception 0E When Creating Sub-Folder on an HPFS Volume"
permalink: /kb/235/Q235711/
---

## Q235711: Fatal Exception 0E When Creating Sub-Folder on an HPFS Volume

{% raw %}

	Article: Q235711
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95; Win2000:95
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork win95kbfixlist
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 95 OEM Service Release, versions 2.0, 2.1, 2.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to create a sub-folder on an HPFS volume from a 16-bit program
	(such as File Manager) after you apply the Microsoft client redirector
	(Vrdrupd.exe, from Q183493, which installs version 4.0.0.1118 of the Vredir.vxd
	file), you may receive the following error message:
	
	  Fatal Exception 0E has occurred at 0028:C027F417 in VxD IFSMGR(04) +
	  00006AEF.
	
	NOTE: The numerical content of the addresses may vary.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time    Version      Size    File name     Platform
	  -------------------------------------------------------------
	  6/17/99   9:06p   4.00.1121   157,285b Vredir.vxd    win95 osr2
	
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows 95 OEM Service Release
	2, 2.1, and 2.5.
	
	MORE INFORMATION
	================
	
	The ability to obtain access to sub-folders on HPFS volumes from 16-bit programs
	was implemented as a Design Change Request for Windows 95 OEM Service Release 2.
	For additional information about this modification, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q183493 Batch File Calling CD Command May Not Run on HPFS
	
	If the modification from Q183493 has not been implemented on a Windows 95-based
	computer, you may receive an "access denied" error message when you try to
	create a sub-folder on an HPFS volume from a 16-bit program. You can avoid the
	"Access denied" error message by applying the hotfix mentioned above.
	
	
	Additional query words: lanman lanman2 winfile w95qfe
	
	======================================================================
	Keywords          : kberrmsg kbnetwork win95 kbfixlist
	Technology        : kbWin95search kbOPKSearch kbZNotKeyword3 kbWin95OPKOSR25 kbWin95OPKOSR210
	Version           : WINDOWS:95; Win2000:95
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
