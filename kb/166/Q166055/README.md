---
layout: page
title: "Q166055: WV: Margins Outside Printable Area Error in Word Viewer"
permalink: /kb/166/Q166055/
---

## Q166055: WV: Margins Outside Printable Area Error in Word Viewer

{% raw %}

	Article: Q166055
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbprint kbusage kbviewer word97 kblayout
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word Viewer 97-2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you try to print a document from Microsoft Word Viewer 97-2000 that has
	margins set outside the printable area for the current printer, the following
	error message appears:
	
	  The margins of section # are set outside the printable area of the page. Do
	  you want to continue?
	
	Choosing Yes prints the page with the possibility of having some text cut off.
	Choosing No cancels the printing of the document.
	
	You are unable to adjust the margins of the document in Microsoft Word Viewer.
	
	CAUSE
	=====
	
	Word Viewer 97-2000 does not have a Page Setup option that allows you to adjust
	the margins of the document.
	
	Word Viewer is only for viewing and printing Word documents. To edit a document,
	you must use Microsoft Word.
	
	WORKAROUND
	==========
	
	To work around this problem, use one of the following methods.
	
	Method 1: Ignore the Error Message
	----------------------------------
	
	Ignore the error by clicking the Continue button.
	
	The document will be printed, but there is a danger that some of the text may be
	truncated in the printed version.
	
	Method 2: Open the Document for Editing in Word
	-----------------------------------------------
	
	Open the document in Microsoft Word and adjust the margins so that the error does
	not occur.
	
	In Word Viewer 97-2000, on the File menu, click Open For Editing. This starts
	Microsoft Word, loads the document, and allows you to make changes.
	
	MORE INFORMATION
	================
	
	Most printers cannot print all the way to the edge of the paper due to physical
	limitations in the printer and the way it handles the paper.
	
	If you set your document margins closer to the edge of the paper than your
	printer is capable of printing, Microsoft Word and Microsoft Word Viewer return
	a warning message for each copy you send to the printer.
	
	Most laser printers, such as the Hewlett-Packard (HP) LaserJet, cannot print
	closer to any edge of the paper than 0.25 inch. Some laser printers, such as the
	HP LaserJet Series II, require 0.5-inch margins. DeskJet printers generally
	cannot print closer to the bottom edge than .67 inch. Most PostScript and
	dot-matrix printers have their own internal printer driver setting for margins.
	
	The unprintable region is determined by the printer that is currently being used.
	To correct the margins that are set to close to the edge of the paper, open the
	document in Microsoft Word and follow these steps:
	
	1. Make sure you are using the same printer driver that gave you the error in
	  Microsoft Word Viewer.
	
	2. In Word, on the File menu, click Page Setup.
	
	3. Click the OK button.
	
	  You see a warning dialog box about the unprintable regions.
	
	4. Click the Fix button.
	
	5. Save and close the document.
	
	You can now open and print the document in Word Viewer without receiving the
	error message.
	
	For more information about Word Viewer 97-2000, please see the following
	Knowledge Base article:
	
	  
	
	  Q165908 WV: How to Obtain Microsoft Word Viewers
	
	Additional query words:
	
	======================================================================
	Keywords          : kbprint kbusage kbviewer word97 kblayout 
	Technology        : kbWordViewerSearch kbViewerSearch kbWordViewer97
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
