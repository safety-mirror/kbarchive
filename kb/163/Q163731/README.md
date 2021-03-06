---
layout: page
title: "Q163731: WD97: Bullets and Horizontal Lines Lost After Save to FTP Server"
permalink: /kb/163/Q163731/
---

## Q163731: WD97: Bullets and Horizontal Lines Lost After Save to FTP Server

{% raw %}

	Article: Q163731
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbualink97 kbwdinternet
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you save an HTML document to an FTP server and then insert graphics
	interchange format (GIF) bullets or horizontal lines into the document, the
	bullet or line images are not copied to the FTP server, and you do not receive a
	warning.
	
	When this occurs, the GIF bullets and horizontal lines are missing from the HTML
	document the next time the document is opened.
	
	CAUSE
	=====
	
	Normally, .gif and .jpg images are copied to the same directory as the document
	when the document is saved. When the document is re-opened, the images are read
	back in and displayed in the document. However, when you save to an FTP server,
	the .gif and .jpg files are saved to the Windows Temp directory instead of the
	directory where the document is being saved. During the initial save to the FTP
	server, you are warned that this may happen; however, on subsequent saves, you
	are not warned.
	
	WORKAROUND
	==========
	
	To work around this problem, manually copy the .gif and .jpg files to the
	directory where the document is saved on the FTP server.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginnning of this article.
	
	MORE INFORMATION
	================
	
	The problem is twofold: first, the .gif and .jpg images are not retained when
	you save to an FTP server; and second, there are some situations where you are
	not warned that this will happen.
	
	Word displays a warning about the images if all of the following are true:
	
	- The save location is not a file allocation table (FAT) or a universal naming
	  convention (UNC) location,
	
	  -and-
	
	- there is at least one embedded image,
	
	  -and-
	
	- the save is the first save of the document.
	
	No warning is displayed if you do the following:
	
	1. Save the document to an FTP server before inserting .gif or .jpg images.
	
	2. Insert the .gif or .jpg images.
	
	3. Update the saved document on the server.
	
	Additional query words: 97 missing
	
	======================================================================
	Keywords          : kbualink97 kbwdinternet 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	
	=============================================================================
	

{% endraw %}
