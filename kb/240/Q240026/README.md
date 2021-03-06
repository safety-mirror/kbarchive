---
layout: page
title: "Q240026: Problems with &quot;Run Only Allowed Windows Applications&quot; Policy"
permalink: /kb/240/Q240026/
---

## Q240026: Problems with &quot;Run Only Allowed Windows Applications&quot; Policy

{% raw %}

	Article: Q240026
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95; Win2000:95
	Operating System(s): 
	Keyword(s): kbenv osr2 win95
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 95 OEM Service Release, versions 1.0, 2.0, 2.1, 2.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If the "Run only allowed Windows applications" system policy is set to allow
	only certain programs to be run in Windows 95, you may receive the following
	error message when you attempt to open a document by double-clicking it in
	Windows Explorer:
	
	  Restrictions
	  This operation has been cancelled due to restrictions in effect on this
	  computer. Please contact your system administrator.
	
	This error message may occur even if the program that opens the document is on
	the list of allowed Windows applications.
	
	CAUSE
	=====
	
	The problem occurs if the path to the program that opens the document (that is,
	the program that is associated with the document's file type) contains spaces,
	but is not enclosed in quotation marks.
	
	This information is located in the registry, under a key of the following form:
	
	  HKEY_CLASSES_ROOT\<file type>\shell\open\command
	
	The path to the program that opens the file type is stored in the (Default) value
	under this key.
	
	RESOLUTION
	==========
	
	To resolve this issue, use either of the following methods:
	
	Method 1
	--------
	
	Install Microsoft Internet Explorer 4.01 Service Pack 1 (SP1) or later, and
	choose to install the Windows Desktop Update component. To obtain Internet
	Explorer, please visit the following Microsoft Web site:
	
	  http://www.microsoft.com/ie
	
	Method 2
	--------
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	On systems that are running an earlier version of Internet Explorer or not
	running Internet Explorer at all, you may be able to work around this problem by
	either surrounding the entire program path with quotation marks, or by altering
	the program path to its equivalent short name (8.3) format. To do this:
	
	1. Start Registry Editor (Regedit.exe).
	
	2. Locate the (Default) value under the following key
	
	  HKEY_CLASSES_ROOT\<file type>\shell\open\command
	
	where <file type> is the file type for the document you are trying to
	open.
	
	3. On the Edit menu, click Modify. Edit the value data to enclose the path to
	  the program in quotation marks, and then click OK.
	
	  For example, if the original value data is:
	
	  C:\Program Files\APP1\Binary Files\APP1.EXE %1
	
	Change the value to either:
	
	  "C:\Program Files\APP1\Binary Files\APP1.EXE" %1 (notice the quotation
	  marks)
	
	  -or-
	
	  C:\PROGRA~1\APP1\BINARY~1\APP1.EXE %1 (no quotation marks needed)
	
	4. Quit Registry Editor.
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q178723 Problems with 'Run Only Allowed Windows Application'
	
	
	Additional query words: w95qfe
	
	======================================================================
	Keywords          : kbenv osr2 win95 
	Technology        : kbWin95search kbOPKSearch kbZNotKeyword3 kbWin95OPKOSR25 kbWin95OPKOSR210
	Version           : WINDOWS:95; Win2000:95
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
