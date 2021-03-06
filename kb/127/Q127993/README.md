---
layout: page
title: "Q127993: PRB: Corrupt Binary File After Merging with SourceSafe"
permalink: /kb/127/Q127993/
---

## Q127993: PRB: Corrupt Binary File After Merging with SourceSafe

{% raw %}

	Article: Q127993
	Product(s): Microsoft SourceSafe
	Version(s): 3.10
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 07-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SourceSafe for Windows, version 3.1 
	- Microsoft SourceSafe for Macintosh, version 3.1 
	- Microsoft SourceSafe for MS-DOS, version 3.1 
	- Microsoft SourceSafe for UNIX, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Binary file is corrupted after a merge is attempted. There are two scenarios
	where a merge can occur:
	
	1. Multiple_Checkouts = Yes in the SRCSAFE.INI or SS.INI file.
	
	-or-
	
	2. A binary file is separated and later merged.
	
	Binary files will become corrupt if SourceSafe attempts to merge these files.
	
	CAUSE
	=====
	
	This is by design. SourceSafe cannot read or edit binary files. These files can
	only safely be edited by the creator application.
	
	RESOLUTION
	==========
	
	To prevent scenario 1, put all binary files in a subproject, and put a
	Multiple_Checkouts=No in the project header for that subproject. This will turn
	off multiple checkouts for this subproject only.
	
	For example, you may want to organize your projects as shown in the documentation
	(User Guide Chapter 2 Overview), with a subproject containing the binary files:
	
	       $/-
	         |
	         TESTDATA
	            |
	             - BINARIES
	
	Such that the following would be a subproject header:
	
	  [$/TESTDATA/BINARIES]
	
	To do this, place the following in the SS.INI file under the subproject header
	for each user:
	
	  Multiple_Checkouts=No
	
	Then only one person can edit that set of files.
	
	To work around scenario 2, use the original application to accomplish the merge
	manually. In some cases, you can get both versions of the file and use the
	application utilities to merge the differences.
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbHWMAC kbOSMAC kbSSafeSearch kbAudDeveloper kbZNotKeyword2 kbZNotKeyword3 kbSSafe310 kbSSafe310DOS kbSSafe310Mac kbSSafe300UNIX
	Version           : 3.10
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
