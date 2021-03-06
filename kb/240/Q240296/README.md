---
layout: page
title: "Q240296: Reference Suite 2000: Error Message When You Start Program"
permalink: /kb/240/Q240296/
---

## Q240296: Reference Suite 2000: Error Message When You Start Program

{% raw %}

	Article: Q240296
	Product(s): Microsoft Home Multimedia Titles
	Version(s): ; WINDOWS:
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbimu
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta Encyclopedia 2000 
	- Microsoft Encarta Reference Suite 2000 
	- Microsoft Encarta Interactive World Atlas 2000 
	- Microsoft Encarta World English Dictionary 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start one of the programs listed at the beginning of this article, you
	may receive one of the following error messages:
	
	Microsoft Encarta Encyclopedia 2000:
	
	  Enc2000 caused an invalid page fault in module Sfc10.ocx.
	
	
	Microsoft Encarta Interactive World Atlas 2000:
	
	  Msref.dll has detected an error in Load From Storage.
	
	  Encarta Interactive World Atlas is unable to continue running. The problem
	  may be the result of low system resources such as memory or disk space. Try
	  closing other running applications or freeing up disk space before restarting
	  Encarta Interactive World Atlas.
	
	Microsoft Encarta World English Dictionary 2000:
	
	  Ewed caused an invalid page fault in module Wheeled.dll.
	
	  Ewed caused an invalid page fault in module Mfc42.dll.
	
	CAUSE
	=====
	
	This behavior can occur if certain files installed by the program are not
	properly registered by Microsoft Windows.
	
	RESOLUTION
	==========
	
	To resolve this issue, use the following methods in the order in which they are
	presented.
	
	Remove and Reinstall the Program
	--------------------------------
	
	To remove and reinstall the program:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. On the Install/Uninstall tab, click the program(s) you want to remove.
	
	  NOTE: When you remove Microsoft Encarta Reference Suite 2000, you remove all
	  of the programs included in the Reference Suite.
	
	4. Clean boot your computer. To clean boot your computer, use the appropriate
	  steps for your version of Windows.
	
	  Microsoft Windows 98:
	
	  a. Click Start, point to Programs, point to Accessories, point to System
	     Tools, and then click System Information.
	
	  b. On the Tools menu, click System Configuration Utility.
	
	  c. On the General tab, click Selective Startup, and then click to clear the
	     following check boxes:
	
	      - Process Config.sys File
	      - Process Autoexec.bat File
	      - Process Winstart.bat File (if available)
	      - Process Win.ini File
	      - Load Startup Group Items
	
	  d. Click OK. When you are prompted to restart the computer, do so.
	
	  NOTE: To restore your original Startup options, click Normal Startup on the
	  General tab in the System Configuration Utility tool.
	
	  For additional information about how to clean boot Windows 98, please see the
	  following article in the Microsoft Knowledge Base:
	
	  Q192926 How to Perform Clean-Boot Troubleshooting for Windows 98
	
	
	  Microsoft Windows 95:
	
	  a. Restart the computer. When you see the "Starting Windows 95" message,
	     press the F8 key, and then select Step By Step Confirmation from the
	     Startup menu.
	
	  b. Press Y at each prompt except for the following two prompts, at which you
	     must press N:
	
	      - Process your startup device driver (CONFIG.SYS) [Enter=Y, Esc=N]?
	
	      - Process your startup command file (AUTOEXEC.BAT) [Enter=Y,Esc=N]?
	
	  c. Quit all running programs except Explorer and Systray. To do this:
	
	     a. Press CTRL+ALT+DELETE.
	
	     b. Click the program you want to quit, and then click End Task.
	
	     c. If you receive a message that the program is busy or not responding,
	        click End Task again.
	
	     Repeat this step until you have quit all programs except Explorer and
	     Systray.
	
	  d. Disable any anti-virus or disk tool programs installed on the computer.
	     For information about how to disable these programs, see the printed or
	     online documentation for the program.
	
	  NOTE: To restore your original Startup options, restart the computer normally,
	  and then enable any anti-virus or disk tool programs that are installed on
	  the computer. For information about how to enable these programs, see the
	  printed or online documentation for the program.
	
	  For additional information about how to clean boot Windows 95, click the
	  article number below to view the article in the Microsoft Knowledge Base:
	
	  Q177604 Multimedia: Troubleshooting Using Clean Boot of Windows 95
	
	  e. Reinstall the program.
	
	
	If the issue continues to occur, proceed to the next method.
	
	Manually Register the Required Files
	------------------------------------
	
	To manually register the files required by the program:
	
	1. Click Start, point to Find, and then click "Files or Folders."
	
	2. In the Named box, type "regsvr32.exe" (without the quotation marks).
	
	3. In the "Look in" box, click My Computer, and then click Find Now.
	
	  NOTE: This step locates the Regsvr32.exe file, which is used in the following
	  steps.
	
	4. Click Start, and then click Run.
	
	5. In the Open box, type the following line, and then click OK:
	
	  C:\Program Files\Common Files\Microsoft Shared\Information Retrieval
	
	6. Drag the following files and drop them on top of the Regsvr32.exe file in the
	  "Find: Files or Folders" window. You should receive a message stating that
	  registration was successful for each file.
	
	  NOTE: You may not see every file in the following list.
	
	   - Itcc51.dll
	   - Itircl51.dll
	   - Itss51.dll
	
	7. In the Open box, type the following line, and then click OK:
	
	  C:\Program Files\Common Files\Microsoft Shared\Reference Titles
	
	8. Drag the following files and drop them on top of the Regsvr32.exe file in the
	  "Find: Files or Folders" window. You should receive a message stating that
	  registration was successful for each file.
	
	  NOTE: You may not see every file listed in the following table.
	
	  +----------------------------------------------------------------------------------------------------------+
	  | File name    | Encarta Encyclopedia | Encarta Interactive World Atlas | Encarta World English Dictionary | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Msref.dll    | No                   | Yes                             | No                               | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Refjic.dll   | Yes                  | Yes                             | Yes                              | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Refmenu.dll  | No                   | Yes                             | No                               | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Refsv.dll    | Yes                  | No                              | No                               | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Sfc10.ocx    | Yes                  | Yes                             | Yes                              | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Treedata.dll | Yes                  | No                              | No                               | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Wheeled.dll  | No                   | No                              | Yes                              | 
	  +----------------------------------------------------------------------------------------------------------+
	  | Wheel2ee.dll | Yes                  | No                              | Yes                              | 
	  +----------------------------------------------------------------------------------------------------------+
	
	Additional query words: multi multi-media media mm ee2k ers2k ewed
	
	======================================================================
	Keywords          : kbenv kberrmsg kbimu 
	Technology        : kbHomeProdSearch kbHomeMMsearch kbEncartaSearch kbEncartaEncycSearch kbEncartaEnCyc2000 kbEncartaReference2000 kbEncartaWorldAtlas2000
	Version           : :; WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
