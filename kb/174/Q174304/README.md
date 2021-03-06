---
layout: page
title: "Q174304: WD97: ODMA Save As Command Does Not Close the Previous Document"
permalink: /kb/174/Q174304/
---

## Q174304: WD97: ODMA Save As Command Does Not Close the Previous Document

{% raw %}

	Article: Q174304
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kb3rdparty kbinterop kbdta word8 word97kbfaq
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use a Document Management System (DMS) with Microsoft Word 97, after
	you click Save As on the File menu and save a Word document with a different
	file name, one of the following symptoms may occur:
	
	Case 1: When You Open a Document
	--------------------------------
	
	When you attempt to open a document, you may receive the following error
	message:
	
	  File name.doc is being used by another user.
	
	  Do you want to make a copy?
	
	NOTE: File name.doc is the name of the file you are trying to open. This error
	message will be displayed if, before you attempt to open the file, another user
	opened File name.doc and used the Save As command to save a copy of it. The
	error message is displayed even if the other user no longer has File name.doc
	open.
	
	You may experience data loss in the original document.
	
	
	Case 2: If You Are Using GroupWise
	----------------------------------
	
	When you click Exit on the File menu with a GroupWise document open, you may
	receive the following error message in Word:
	
	  GroupWise error 8201 - cannot return document to library
	
	
	CAUSE
	=====
	
	This problem occurs because Microsoft Word may not correctly close the original
	document when you use the Save As command to save the document with another file
	name.
	
	During the "Save As" process, Word looks for a drawing object in the document. If
	the document lacks a drawing object, the document is not closed correctly.
	
	
	NOTE: After you quit Microsoft Word or close the newly created document (the
	document you created using the Save As command with File name.doc), the original
	document is closed correctly.
	
	RESOLUTION
	==========
	
	To correct this problem, obtain Microsoft Word 97 for Windows, Service Release 2
	(SR-2). For additional information about Service Release 2, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q151261 OFF97: How to Obtain and Install MS Office 97 SR-2
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.<A0>This problem was corrected in Microsoft
	Office 97 for Windows, Service Release 2 (SR-2).
	
	MORE INFORMATION
	================
	
	If you previously installed a macro to work around the problem, or if you
	installed the Saveas.dot template provided by Microsoft Technical Support, you
	may want to remove the macros.
	
	NOTE: If your version of Word was installed with the "Run From Network Server"
	option, contact your network administrator to complete these steps.
	
	To remove the macros, follow these steps:
	
	1. Open the Normal.dot file. By default, the Normal.dot file is located in the
	  following folder:
	
	Microsoft Windows 95, Microsoft Windows 98:
	
	  C:\Program Files\Microsoft Office\Templates
	
	Microsoft Windows 95 and Microsoft Windows 98 with Profiles Enabled, or Microsoft
	Windows NT 4.0:
	
	  C:\WindowsFolder\Profiles\UserName\Application Data\Microsoft\Templates
	
	Microsoft Windows 2000:
	
	  C:\Documents and Settings\UserName\Application Data\Microsoft\Templates
	
	2. On the Tools menu, point to Macro, and then click Macros.
	
	3. Select the Document_open macro, and then click Delete.
	
	4. Close Word. If prompted, save the changes to Normal.dot. If you are unable to
	  save the changes to Normal.dot, contact your network administrator.
	
	Additional query words: saveas saveas.dot pcdocs PC DOCS ODMA DMS Missing edits changes lost corrupt damaged lose novell
	
	======================================================================
	Keywords          : kb3rdparty kbinterop kbdta word8 word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
