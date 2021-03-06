---
layout: page
title: "Q85413: MS-DOS 5.0a Upgrade README.TXT: Hardware Compatibility"
permalink: /kb/085/Q85413/
---

## Q85413: MS-DOS 5.0a Upgrade README.TXT: Hardware Compatibility

{% raw %}

	Article: Q85413
	Product(s): Microsoft Disk Operating System
	Version(s): 5.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 5.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information was taken from the Microsoft MS-DOS 5.0a Upgrade
	README.TXT file.
	
	MORE INFORMATION
	================
	
	5. MAKING YOUR HARDWARE COMPATIBLE WITH MS-DOS 5.0
	--------------------------------------------------
	
	5.1 Acer 1100/33 and CTRL+ALT+DEL:
	
	If you have an Acer 1100/33 computer with an Award BIOS, you may not be able to
	restart your system by using CTRL+ALT+DEL. Contact Acer for a ROM BIOS upgrade.
	
	5.2 Amstrad Systems and KEYB.COM:
	
	If your Amstrad system has a ROM BIOS version earlier than 1.4, and you can't use
	your keyboard after loading KEYB.COM, contact your vendor for a ROM BIOS
	upgrade.
	
	5.3 Apricot Qi 386 Systems:
	
	If your Apricot Qi 300 fails to start while loading EMM386.EXE, contact Apricot
	for a ROM BIOS upgrade.
	
	Some Apricot Qi660 and Qi900 computers may not work if MS- DOS 5.0 is loaded into
	the high memory area. Run MS-DOS 5.0 in conventional memory, or contact Apricot
	Computers for more information.
	
	5.4 AT&T Computer with an VDC 750 Display Adapter Card:
	
	Before using the MS-DOS Shell Task Swapper on an AT&T computer with a VDC 750
	display adapter card, remove the DEVICE=EGA.SYS command from your CONFIG.SYS
	file.
	
	5.5 Compaq EXTDISK.SYS Driver:
	
	Compaq EXTDISK.SYS driver version 3.00 or later is compatible with MS-DOS 5.0.
	Contact your vendor for an upgrade.
	
	5.6 Corel Corporation Disk Drivers:
	
	If your Corel Corporation disk driver doesn't work correctly, contact your vendor
	for an upgrade.
	
	5.7 External Floppy Disk Drives:
	
	If you can't use your Nth, Procomm, or Sysgen external floppy disk drive, contact
	your vendor for an update.
	
	5.8 Hardcard:
	
	a. Hardcard II
	
	  If you can't use Plus Development Hardcard II or Hardcard II XL when running
	  EMM386.EXE, specify the exclude (x=) switch to prevent EMM386 from
	  conflicting with the card's BIOS address.
	
	  See your Hardcard II manual to determine which address space to exclude. See
	  the MS-DOS User's Guide and Reference for more information about the exclude
	  switch.
	
	b. Hardcard 40 or Passport
	
	  If you are using Hardcard 40 or a Passport removable disk, and you have a
	  DEVICE command for PLUSDRV.SYS in your CONFIG.SYS file before upgrading to
	  MS-DOS 5.0:
	
	  1. Disable or remove the DEVICE command for PLUSDRV.SYS command line in your
	     CONFIG.SYS file.
	
	  2. Run MS-DOS 5.0 Setup.
	
	  3. Reenable or return the DEVICE command for PLUSDRV.SYS in your CONFIG.SYS
	     file. Make it the last line in the file.
	
	5.9 IBM PS/1, installing MS-DOS 5.0:
	
	If your IBM PS/1 stops running after MS-DOS version 5.0 is installed, do the
	following:
	
	1. Press and hold down both mouse buttons.
	
	2. Start your PS/1.
	  The computer displays the System menu.
	
	3. From the System menu, choose the Your Software icon.
	  A group of folders appears.
	
	4. Choose the DOS folder.
	  A list of the files in your DOS folder appears.
	
	5. Double-click the CUSTOMIZ file.
	  The How System Starts screen appears.
	
	6. Use the DOWN ARROW key to select the Try Diskette First, Then Try Fixed Disk
	  option.
	
	7. Press the SPACEBAR to choose the option.
	
	8. Use the DOWN ARROW key to select the Read CONFIG.SYS option.
	
	9. Use the RIGHT ARROW key to select the From Disk option.
	
	10. Press the SPACEBAR to choose the option.
	
	11. Use the DOWN ARROW key to select the Read AUTOEXEC.BAT option.
	
	12. Use the RIGHT ARROW key to select the From Disk option.
	
	13. Press the SPACEBAR to choose the option.
	
	14. Press enter to save the system startup changes.
	
	15. Restart your computer by pressing CTRL+ALT+DEL.
	
	5.10 NCR VGA BIOS:
	
	If you have an NCR VGA BIOS and can't switch between screens when running MS-DOS
	Shell or QBasic, see your NCR manual for information about making your VGA BIOS
	PS/2 compatible.
	
	5.11 Olivetti System with a CGA Video Board:
	
	An Olivetti system with a CGA video board may not scroll correctly. Add the /s
	switch to the DEVICE=ANSI.SYS command in your CONFIG.SYS file.
	
	5.12 Toshiba T3100SX:
	
	Toshiba T3100SX computer's suspend/resume feature is incompatible with
	EMM386.EXE. Either disable the feature or do not use EMM386.EXE.
	
	5.13 Western Digital VGA Card:
	
	If you have a Western Digital VGA card and are using RAMBIOS.EXE and RAMBIOS.SYS,
	load RAMBIOS.SYS before ANSI.SYS and DISPLAY.SYS in your CONFIG.SYS file, and
	RAMBIOS.EXE before GRAPHICS.COM in your AUTOEXEC.BAT file.
	
	5.14 ATI WonderCard 3.x:
	
	Using MS-DOS 5.0 with an ATI WonderCard may cause the lower part of your display
	to be truncated. To solve this problem, type the following command before
	running Setup:
	
	  " SMS EGABIOS" (without the quotation marks)
	
	Or obtain an updated ROM BIOS for the card.
	
	5.15 XGA and EMM386.EXE:
	
	If you use an XGA display with EMM386.EXE, you may need to exclude certain memory
	ranges with the EMM386 EXCLUDE option (x=). To determine which memory ranges to
	exclude, use the reference disk that came with your computer to view the memory
	map.
	
	5.16 Zenith Computer:
	
	To use the GRAPHICS command with a Zenith computer, set the STACKS command in
	your CONFIG.SYS file to at least STACKS=9,256. For information about the STACKS
	command, see Chapter 14 of the MS-DOS User's Guide and Reference.
	
	5.17 Zeos 486 and Task Swapper:
	
	If you have a Zeos 486 computer with a Mylex BIOS, you may not be able to use
	Task Swapper in MS-DOS Shell. Contact Zeos for a ROM BIOS upgrade.
	
	
	Additional query words: 5.00a update noupd
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS500a
	Version           : :5.0a
	
	=============================================================================
	

{% endraw %}
