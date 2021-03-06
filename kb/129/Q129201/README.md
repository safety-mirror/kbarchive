---
layout: page
title: "Q129201: PC MMTA: OS/2 Version 1.3 Installation Issues"
permalink: /kb/129/Q129201/
---

## Q129201: PC MMTA: OS/2 Version 1.3 Installation Issues

{% raw %}

	Article: Q129201
	Product(s): Microsoft Mail For PC Networks
	Version(s): 3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Multitasking MTA, version 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you install the OS/2 version 1.3 system software (included with the Mail
	Multitasking version 3.2), and you encounter an error, the most likely cause is
	a system or hardware problem.
	
	Below are three examples of the most common errors, along with their causes and
	solutions.
	
	1. SYS1733 error
	
	  This error message may be displayed during installation. A SYS1733 occurs
	  because the country information file A:\COUNTRY.SYS is incorrect; the system
	  has stopped.
	
	  This error explanation is likely misleading as it rarely explains the cause.
	
	  See the Cause section below for likely reasons for this error.
	
	2. Fdisk Unsuccessful or Cannot Locate Fixed Disk Drive errors
	
	  One or both of these errors occur when the hard drive and/or adapter require a
	  .BID file not included on the Installation disks A and B.
	
	3. Looping on reboot after installation
	
	  After you install OS/2 and reboot your system, the computer reboots in an
	  infinite loop until you insert a bootable floppy.
	
	CAUSE
	=====
	
	1. SYS1733 error
	
	  The error stems from a hardware configuration problem. Known causes are:
	
	   - Misconfigured CMOS for the floppy disk drives.
	
	   - Missing one of two floppy disk drives, but CMOS states both exist.
	
	   - Incorrect SCSI configurations.
	
	2. Fdisk Unsuccessful or Cannot Locate Fixed Disk
	
	  The installation requires a special .BID file not included with the OS/2
	  installation disks A and B. A BID file is a Layered Device Driver
	  Architecture (LADDR) driver for hard drives and adapters. Some PC computer
	  hardware manufacturers require a proprietary .BID file.
	
	3. Looping on reboot after installation
	
	  The most likely cause is selecting the wrong mouse driver during the
	  installation process.
	
	RESOLUTION
	==========
	
	1. SYS1733 error
	
	  To see if your CMOS is configured incorrectly, check your computer's BIOS
	  setup parameters and verify they match the drives physically installed. To
	  see if you have a misconfigured SCSI adapter card check the card's settings
	  against the documented settings in the adapter's installation manual.
	
	2. Fdisk Unsuccessful or Cannot Locate Fixed Disk errors
	
	  To resolve the error and complete installation, try the following steps:
	
	   - If you used Installation Disk A to boot the PC, try Installation Disk B
	     and vice versa. This will insure that all .BID files have been tried and
	     tested.
	
	   - Contact the disk adapter manufacturer and request a .BID file for the
	     adapter model. Once the .BID file is obtained you must:
	
	     a. Make a copy of your Installation disk A
	
	     b. Delete all the .BID files on the disk A copy
	
	     c. Copy the new .BID file to the disk A copy
	
	     d. Rename the new file to BOOTBID.BID.
	
	   - Reboot the computer with the newly modified Installation disk and proceed
	     with installing OS/2.
	
	3. Looping on reboot after installation
	
	  Reboot OS/2 using the Installation disk and select the appropriate mouse
	  driver for your configuration. If the problem persists, edit the CONFIG.SYS
	  and remark out the suspect mouse driver as shown:
	
	  rem DEVICE=C:\OS2\MOUSE.SYS TYPE MSSER$
	
	  Reboot the OS/2 computer.
	
	MORE INFORMATION
	================
	
	The information in this article only pertains to Microsoft's OS/2 version 1.3,
	included with the Microsoft Mail Multitasking MTA version 3.2.
	
	Additional query words: 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailMMTA320
	Version           : :3.2
	
	=============================================================================
	

{% endraw %}
