---
layout: page
title: "Q294704: PRB: VC ClassView Doesn't Show Classes Defined in Header File"
permalink: /kb/294/Q294704/
---

## Q294704: PRB: VC ClassView Doesn't Show Classes Defined in Header File

{% raw %}

	Article: Q294704
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbVC kbVC600 kbDSupport
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Editions, version 6.0 
	- Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	Classes defined in a header file are not being displayed in ClassView in Visual
	c++ version 6.0 and Class View in Visual C++ .NET.
	
	CAUSE
	=====
	
	Any of the following could cause this problem:
	
	1. A header file extension may be different from the product convention (.h, for
	  example).
	
	2. The Class View database file .ncb may have become corrupted.
	
	3. A second instance of Visual C++ may be running with the same project loaded.
	
	4. The Class View database file .ncb has the read-only attribute selected.
	
	5. The project may have been saved to a removable drive.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	The following solutions correspond to the specific causes noted above:
	
	1. Add extensions (if you are using other extensions for header files like .hh)
	  to the registry key:
	
	  HKCU\Software\Microsoft\DevStudio\6.0\Text Editor\Tabs/Language
	  Settings\C/C++
	
	  For Visual C++ .NET, add the extension (including the .) to NCB Default C/C++
	  Extensions in:
	
	  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\7.0\Languages\Language
	  Services\C/C++
	
	2. If the Class View database file .ncb is corrupt, close the workspace or
	  solution, delete the .ncb file, and then reopen the workspace.
	
	3. Check to see if there is a second instance of Visual C++ running that has the
	  same project loaded. If the second instance is visible, simply close it.
	  However, the second instance may be hidden. If so, use Task Manager or PView
	  to close that instance.
	
	4. Check whether the ClassView database file .ncb has the read-only attribute
	  selected. Visual C++ must have write access. Remove the read-only attribute.
	
	  This may include removing the file from Source Code Control, or checking it
	  out if that is not possible.
	
	5. If the project is being saved to a removable drive, save the project to the
	  local hard drive and see if the problem still occurs.
	
	MORE INFORMATION
	================
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q181506 HOWTO: Make VC++ Recognize File Extensions as C/C++ Files
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVC kbVC600 kbDSupport 
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch kbVCNET
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
