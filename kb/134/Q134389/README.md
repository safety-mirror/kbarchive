---
layout: page
title: "Q134389: Setup Cannot Find Previous Version of Windows NT"
permalink: /kb/134/Q134389/
---

## Q134389: Setup Cannot Find Previous Version of Windows NT

{% raw %}

	Article: Q134389
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you attempt to upgrade an exiting Windows NT installation to Windows NT 3.5
	or 3.51, an error may appear stating that Windows NT Setup could not find an
	existing version of Windows NT. You can only exit Setup or install Windows NT
	into a new directory.
	
	CAUSE
	=====
	
	This problem occurs because Setup looks for SCSI instead of MULTI in the
	BOOT.INI file.
	
	Setup fails to find standard Windows NT 3.1 installations that have SCSI in the
	BOOT.INI file, and fails to find Windows NT 3.5 installations where you have
	changed the MULTI references to SCSI in the BOOT.INI file.
	
	WORKAROUND
	==========
	
	To work around this problem, add a extra line in the BOOT.INI file that points
	to the install to be upgraded. Use MULTI instead of SCSI.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT versions 3.5 and 3.51
	We are researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	
	=============================================================================
	

{% endraw %}
