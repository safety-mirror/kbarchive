---
layout: page
title: "Q76792: MS-DOS Setup Repeatedly Asks for the Same Disk"
permalink: /kb/076/Q76792/
---

## Q76792: MS-DOS Setup Repeatedly Asks for the Same Disk

{% raw %}

	Article: Q76792
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to install MS-DOS, Setup repeatedly asks for a disk that you
	already inserted in the floppy disk drive. Or, Setup displays the following
	message when you insert the Uninstall disk in drive A:
	
	  ERROR
	  This is not the correct disk.
	  Press ENTER to continue.
	
	CAUSE
	=====
	
	Setup may repeatedly ask for a disk for several reasons:
	
	- The disk is a copy of an original Upgrade disk, and the copy does not have
	  the volume label of the original.
	
	- The disk you are using for the Uninstall procedure is incorrectly formatted.
	
	- The device driver that controls your floppy disk drive is not reporting that
	  the drive door is closed after you insert a floppy disk.
	
	- Your system is infected with a virus.
	
	RESOLUTION
	==========
	
	If Setup Repeatedly Asks for an Upgrade Disk
	--------------------------------------------
	
	If Setup repeatedly asks for an Upgrade disk, and the disk is a copy you made, do
	the following:
	
	1. Insert the disk into drive A or B.
	
	2. Type the following
	
	  " dir <drive letter>: /p" (without the quotation marks)
	
	  where <drive letter> is the drive you placed the disk in.
	
	3. Check to make sure the volume label includes the word "Disk," followed by six
	  spaces and the correct number of the disk. For example, if the disk is
	  Upgrade Disk 3, MS-DOS should display the following message:
	
	     Volume in drive A is DISK      3
	
	4. If there are not exactly six spaces between "Disk" and the disk number, or if
	  the disk number is incorrect, type
	
	  " label <drive letter>:" (without the quotation marks)
	
	  where <drive letter> is the drive you placed the disk in.
	
	5. When MS-DOS prompts you for a volume label, type the correct label.
	
	If Setup Repeatedly Asks for the Uninstall Disk
	-----------------------------------------------
	
	If Setup repeatedly asks for the Uninstall disk, use an unformatted disk. If
	using an unformatted disk does not work, do the following:
	
	1. Insert an unformatted disk into drive A.
	
	2. Type the following:
	
	  " format a: /s" (without the quotation marks)
	
	  MS-DOS formats the disk in drive A and transfers system files to it.
	
	3. Type the following, substituting a value listed in the following table for
	  <x> and pressing ENTER at the end of each line
	
	  " copy con a:config.sys
	  drivparm=/d:0 /f:<x> /c" (without the quotation marks)
	
	  where number assigned to the /d drivparm switch specifies the physical drive
	  number. Drive A is 0, drive B is 1, drive C is 2, and so on.
	
	  The value of <x> depends on the type of disk drive you are using. The
	  following table lists valid values:
	
	     Drive size      Disk capacity      Values to use
	     ------------------------------------------------
	
	     5.25-inch       160K, 180K,         0
	                     320K, 360K
	     5.25-inch       1.2 MB              1
	     3.5-inch        720K                2
	     3.5-inch        1.44 MB             7
	     3.5-inch        2.88 MB             9
	
	4. Press F6.
	
	5. Restart your computer by pressing CTRL+ALT+DEL.
	
	6. Insert MS-DOS 5.0 Upgrade Disk 1 into drive A.
	
	7. Type the following:
	
	  " a:setup" (without the quotation marks)
	
	  Follow the instructions on your screen.
	
	8. If Setup still does not accept the Uninstall disk, run a virus-scanning
	  program. If you have MS-DOS 6 or later Upgrade, you can run Microsoft
	  Anti-Virus (MSAV.EXE). To do so, boot your computer from MS-DOS Setup Disk 1,
	  insert Disk 3 of the 3.5-inch 1.44 megabyte (MB) disk set or Disk 4 of the
	  5.25-inch 1.2 MB disk set, and run MSAV. You receive an error message when
	  MSAV attempts to write to the write-protected disk. You can choose Fail and
	  ignore the message.
	
	9. If the same disk is still repeatedly asked for, do the following:
	
	  a. Make a temporary directory on your hard disk drive.
	
	  b. Copy the installation disks to the temporary directory.
	
	  c. Change the MS-DOS command prompt to the temporary directory.
	
	  d. Run Setup from that directory.
	
	  e. When Setup is complete, delete the temporary directory.
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
