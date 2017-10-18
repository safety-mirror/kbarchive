---
layout: page
title: "Q84339: LANtastic Notes on Version 4.x and Windows 3.1"
permalink: kb/084/Q84339/
---

## Q84339: LANtastic Notes on Version 4.x and Windows 3.1

	Article: Q84339
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information from the "LANtastic Network Operating System
	Version 4 Compatibility Bulletin" for Microsoft Windows operating system version
	3.1. The complete bulletin is available from LANtastic support.
	
	MORE INFORMATION
	================
	
	SMARTDRV.EXE and LANCACHE
	-------------------------
	
	Windows 3.1's Setup will install SMARTDRV.EXE in the AUTOEXEC.BAT file (and maybe
	the CONFIG.SYS depending on hard drive type). This will conflict with the
	LANtastic's LANCache, which is normally loaded in the STARTNET.BAT file located
	in the AUTOEXEC.BAT file.
	
	To disable the LANCache utility, open your STARTNET.BAT (or other batch file that
	starts the network) and delete the following line:
	
	       C:\LANTASTI\LANCACHE
	
	According to LANtastic, it is possible to configure the LANCache for use with
	Windows, instead of using SMARTDrive. For more information, refer to the
	LANtastic manual.
	
	Printing with Windows 3.1
	-------------------------
	
	If you are running Windows 3.1 on a workstation that also functions as a print
	server, then use the following steps to improve printing speed:
	
	1. At the MS-DOS command prompt, run the LANtastic NET_MGR program and choose
	  Shared Resource Management from the Main Functions menu.
	
	2. Select the printer resource (for example @PRINTER), select the Chars/Second
	  field, and change it to 9600.
	
	3. Press the ESC key twice to return to the Main Functions menu, then choose the
	  Server Startup Parameters option. Set Printer Tasks to 1, even if you have
	  more than one printer physically attached to this machine. Exit from NET_MGR
	  and reboot.
	
	With Windows 3.1, you can send print jobs to any of the standard print devices
	(LPT1, LPT2, LPT3, COM1, COM2) when running LANtastic. However, if the printer
	you are sending jobs to is a network printer, do the following to streamline
	printing:
	
	1. Run Control Panel and choose Printers.
	
	2. Clear the Use Print Manager check box.
	
	3. Choose the Connect button and clear the Fast Printing Direct To Port box.
	
	4. Change the Device Not Selected to 900, and change the Transmission Retry
	  Timeout to 950.
	
	5. You must use the LANtastic NET USE command to capture the port you print to
	  before starting Windows. For example:
	
	  net use lpt2: \\server_name\@printer
	
	Standard Mode NetHeapSize Error
	-------------------------------
	
	If you upgraded from Windows 3.0 to Windows 3.1, then you may receive a
	NetHeapSize error when running Windows in standard mode. To correct this, edit
	the SYSTEM.INI file with an ASCII text editor (such as Notepad) by locating the
	[standard] section in SYSTEM.INI and changing NetHeapSize=64 to NetHeapSize=63.
	
	Note: There is also a NetHeapSize setting in the [386Enh] section. You want to
	change the NetHeapSize setting in the [standard] section.
	
	Swap File and SERVER Program
	----------------------------
	
	You cannot set up a permanent swap file on a workstation running the SERVER
	program. To shut down the SERVER program:
	
	1. Exit Windows and type SERVER/REMOVE at the MS-DOS command prompt (do not do
	  this from within Windows).
	
	2. Restart Windows and run Control Panel.
	
	3. Choose the 386 Enhanced icon and adjust the virtual memory.
	
	Note: If you receive the following error message, then you must remark the SERVER
	software in your STARTNET.BAT file and reboot to set up a permanent swap file:
	
	  ERROR: not safe to REMOVE, Interrupts re-hooked
	
	Adapters and Ranges to Be Excluded
	----------------------------------
	
	Windows 3.1's Setup inserts the following line in the [386Enh] section of the
	SYSTEM.INI file during the configuration process:
	
	       EMMExclude=D800-DFFF
	
	Note: If you are using EMM386.EXE, you must use the X= parameter to exclude this
	range also:
	
	       DEVICE=C:\WINDOWS\EMM386.EXE X=D800-DFFF
	
	This prevents Windows from using the default RAMBASE address of the Artisoft
	Enhanced 2Mbps (E2Mbps) adapter. You may remove this line if you are using
	Artisoft AE-2, AE-2/T, AE-3, or AE-1 adapters because they do not use a RAMBASE
	address. If you do have the E2Mbps adapter, verify the address it uses and
	change the values on the EMMExclude line to match them if necessary. If you are
	using adapter cards other than Artisoft's, check the adapter documentation to
	confirm whether the card uses a RAMBASE address.
	
	Additional query words: 3.10 3.11 3rdparty
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	