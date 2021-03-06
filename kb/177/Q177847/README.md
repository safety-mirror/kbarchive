---
layout: page
title: "Q177847: Error Message: Rundll32 Caused a Fault in Setupx"
permalink: /kb/177/Q177847/
---

## Q177847: Error Message: Rundll32 Caused a Fault in Setupx

{% raw %}

	Article: Q177847
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbhw win95 kbHardware
	Last Modified: 24-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you double-click Add New Hardware in Control Panel, you may receive the
	following error message:
	
	  Rundll32 caused a General Protection Fault in module Setupx.dll.
	
	CAUSE
	=====
	
	You may receive this error message if there is a damaged .inf file in the
	Windows\Inf folder.
	
	RESOLUTION
	==========
	
	To resolve this issue, find and delete the damaged .inf file in the Windows\Inf
	folder. To do so, follow these steps:
	
	1. Verify that you can view hidden and system files.
	
	For additional information about how to do this, click the article number below
	to view the article in the Microsoft Knowledge Base:
	
	  Q141276 How to View System and Hidden Files in Windows
	
	2. Determine the date of your original Windows system files. To do so, follow
	  these steps:
	
	  a. Click Start, point to Find, and then click "Files Or Folders".
	
	  b. In the Named box, type "win.com" (without the quotation marks), and then
	     click "Find Now".
	
	  c. Right-click the Win.com file in your Windows folder, and then click
	     Properties.
	
	  d. Note the date on the Modified line. This is the date of your original
	     Windows system files.
	
	3. Click Start, point to Find, and then click "Files Or Folders".
	
	4. In the Named box, type "inf" (without the quotation marks), and then click
	  Find Now.
	
	5. Double-click the Inf folder.
	
	6. Move all of the .inf files that do not have the same date as your original
	  Windows system files into a new folder. For information about how to create a
	  new folder, click Start, click Help, click the Index tab, type "creating
	  folders" (without the quotation marks), and then click Display. For
	  information about how to move files, click Start, click Help, click the Index
	  tab, type "moving files" (without the quotation marks), and then click
	  Display.
	
	7. Click Start, point to Settings, and then click Control Panel.
	
	8. Double-click Add New Hardware, and follow the instructions on the screen. If
	  you do not receive the error message, skip to step 10.
	
	9. If you receive the error message when you run the Add New Hardware wizard,
	  move the .inf files back into the Inf folder, and then reinstall Windows 95.
	
	For additional information about how to reinstall Windows 95, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q149712 How to Install Windows 95: Helpful Tips and Suggestions
	
	10. If you do not receive the error message when you run the Add New Hardware
	  wizard, the damaged .inf file is one of the files you moved in step 6. To
	  identify the damaged .inf file, move the .inf files back into the Inf folder
	  one at a time (noting the name of the .inf file you are moving), and then
	  repeat steps 7-8. Repeat this process until you receive the error message
	  again. When you receive the error message again, the last .inf file you
	  moved is the damaged .inf file. To determine where this file originated,
	  double-click the file and note any manufacturer, version, or date
	  information that may indicate the origin of the file. After you determine
	  the origin of the file, delete the file, and then reinstall it from the
	  original installation disks or CD-ROM.
	
	MORE INFORMATION
	================
	
	.Inf files are text files that contain setup information that is needed to
	install hardware.
	
	For more information about issues with .inf files, see the following articles in
	the Microsoft Knowledge Base:
	
	  Q137377 Removing Drivers from Wizard Hardware Lists
	
	  Q139206 Hardware List Not Updated After Installing New .inf File
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          : kbenv kberrmsg kbhw win95 kbHardware 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : :
	
	=============================================================================
	

{% endraw %}
