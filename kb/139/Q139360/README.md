---
layout: page
title: "Q139360: INFO: Readme.wri: Section 4, Documentation Notes"
permalink: /kb/139/Q139360/
---

## Q139360: INFO: Readme.wri: Section 4, Documentation Notes

{% raw %}

	Article: Q139360
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe400 kbVBp400
	Last Modified: 07-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article holds section 4, Documentation Notes, of the Readme.wri file
	shipped with Visual SourceSafe. For more information about other sections of the
	Readme.wri file, please see the following articles in the Microsoft Knowledge
	Base:
	
	  Q139358 Readme.wri: Section 1.Software Installation Information
	
	  Q139359 Readme.wri: Section 2, General Notes and Tips
	
	  Q139361 Readme.wri: Section 3, Issues and Considerations
	
	  Q139362 Readme.wri: Section 5, New Features of Visual SourceSafe
	
	
	MORE INFORMATION
	================
	
	Chapter 1 - Network Installation
	--------------------------------
	
	The Microsoft SourceSafe User's Guide does not describe the Network Installation
	in detail. See Section 1 of this document for more information.
	
	Chapter 1 - Removing Visual SourceSafe or Components
	----------------------------------------------------
	
	The Microsoft SourceSafe User's Guide does not describe the procedure for
	removing Visual SourceSafe components, or the program or database. See Section 1
	of this document for more information.
	
	Chapter 5 - Using Labels
	------------------------
	
	The section, "Using Labels," in Chapter 5, page 63, does not describe the Item
	edit box in the Label dialog box. Type the name of the item (project or file)
	that you want to label.
	
	Chapter 8 - Correction to Access Rights Table
	---------------------------------------------
	
	The table of access rights for commands, page 116, states that for the Move
	Project command, you need only Add rights. It should state that you need Destroy
	rights in the project you are moving from.
	
	Chapter 8 - Typo in File Extension, Incorrect Use of /D Option
	--------------------------------------------------------------
	
	The sections "Using Separate Icons for Each Database," on page 134, and "Multiple
	SRCSAFE.INI Files," on page 135 both have the following typographical error:
	
	  the C:\VSS\WIN32\SSEXP.EXE file appears as C:\VSS\WIN32\SSEXP.EXT.
	
	Also on page 135, the second sentence in the second paragraph and the example
	that follows it use the /D command line option incorrectly. The option can not
	be used in the following manner, with a directory immediately following the
	option: /D\DATA2. You must set an initialization variable to use /D. Correct use
	of the option is shown in the next section, "Multiple Data_Path Settings."
	
	Appendix B - Description of Treatment of .FRM and .FRX Files Incorrect
	----------------------------------------------------------------------
	
	The section, "Visual SourceSafe and Visual Basic," on page 154, contains an
	incorrect description of Visual SourceSafe's treatment of .frx files associated
	with .frm files. When you check out an .frm file, if there is an .frx file
	associated with it, that .frx file is not checked out. See Section 3.8 for more
	information.
	
	Appendix C - Typo in Description of DELTA_SS.EXE Example
	--------------------------------------------------------
	
	The section, "Converting a Single File or Directory," on page 174, contains the
	following typographical error in the description of the example: "In this
	example, the -r option provides a verbose report of the conversion" The
	description should read, "In this example, the -v option provides a verbose
	report of the conversion ..."
	
	Appendix C - Testlock.exe Syntax
	--------------------------------
	
	The Testlock.exe section in Appendix C, page 178, does not provide a syntax
	statement for Testlock.exe, although a verbal explanation is provided. The
	syntax is:
	
	  TESTLOCK <directory in which Visual SourceSafe was installed>
	
	The Testlock.exe program is in the Win or Win32 directory under the directory in
	which the Visual SourceSafe server setup was installed.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbVBp400 
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
