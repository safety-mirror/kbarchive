---
layout: page
title: "Q76677: How to Determine if BIOS Reports Floppy Drive Type Correctly"
permalink: /kb/076/Q76677/
---

## Q76677: How to Determine if BIOS Reports Floppy Drive Type Correctly

{% raw %}

	Article: Q76677
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	MS-DOS determines the number and type of floppy drives on a system using the ROM
	BIOS services, called interrupts. The MS-DOS DEBUG utility can be used to "ask"
	the ROM BIOS for this information directly. This is helpful in determining why
	MS-DOS may not be accessing a floppy drive or drives correctly.
	
	It is possible that one version of MS-DOS might access a drive and another
	version may not. Some hardware manufacturers modify their MS-DOS to ignore the
	information returned from the ROM BIOS and rely on vendor-specific information
	about the drives.
	
	Early versions of Microsoft MS-DOS make assumptions about the existence of one or
	more floppy drives that might, coincidentally, be correct. However, in Microsoft
	MS-DOS versions 4.0 and later, MS-DOS correctly relies on the information
	reported by the ROM BIOS.
	
	The following procedure uses function 8 of interrupt 13 to determine disk
	parameters. The number of sectors per track and tracks is returned, which
	correlates between the information returned and the parameters MS-DOS uses for
	the FORMAT utility. On AT and PS/2 systems, a drive type code is returned as
	well.
	
	If the BIOS is not returning the correct drive information on an AT or PS/2
	machine, it may indicate that the drive type has not been set properly in the
	CMOS setup. On any machine, it may indicate that the drive is not properly
	installed, or that the drive is not supported by the ROM BIOS. For information
	about your ROM BIOS and whether you need to upgrade, contact your machine or
	BIOS manufacturer.
	
	MORE INFORMATION
	================
	
	To start the DEBUG utility, type "debug" (without the quotation marks) at the
	command prompt and press ENTER. If at any time you wish to exit and start over,
	use the Q[uit] command to exit back to MS-DOS. It is recommended that DEBUG not
	be used when other programs are active or in a multitasking environment such as
	Microsoft Windows.
	
	DEBUG
	Displays        Enter           To
	--------        -----           --
	
	-               a 100           Begin entering commands at address 100
	XXXX:0100       int 13          Do an interrupt 13
	XXXX:0102       int 20          An interrupt 20 here (insurance)
	XXXX:0104       ENTER           Press ENTER here
	-               rip             Display and modify the IP register
	IP XXXX
	:               0100            Begin executing at 100
	-               rax             Display and modify AX register
	AX 0000
	:               0800            Function 8 (get drive information)
	-               rdx             Display and modify DX register
	DX 0000
	:               <drive>         Enter 0 for first floppy, 1 for
	                                second, and so on
	-               p               Process
	
	At this point, DEBUG will execute the command at 0100, interrupt 13. The ROM BIOS
	routine will process interrupt 13, function 8, on the drive you specified, and
	return some information in the registers. DEBUG will display something like
	this:
	
	AX=0000  BX=0002  CX=4F0F  DX=0102  SP=FFEE  BP=0000  SI=0000  DI=2115
	DS=0E77  ES=F000  SS=0E77  CS=0E77  IP=0102   OV UP EI NG NZ NA PO NC
	0E77:0102 CD20          INT     20
	
	The name of each register is displayed, along with its current value. All values
	are in hexadecimal. Note that each X register can also be addressed by its
	"high" and "low" halves; that is, if CX=4F0F, CH=4F and CL=0F.
	
	The flags register is displayed differently. The status of the flags register is
	the series of two-letter codes at the end of the second line. Note the value of
	the last flag on the second line. If it is CY (CarrY), the carry flag was set by
	the BIOS, which means the interrupt failed. In this case, AX= an error value.
	See page 54 of the "IBM ROM BIOS Quick Reference" guide for information about
	these errors. If the last flag is NC (no carry), the carry flag was not set,
	which indicates that the interrupt worked correctly.
	
	On AT and PS/2 systems, the low byte of the BX register (BL) will contain the
	drive type 01 if 360, 02 if 1.2, 03 if 720, and 04 if 1.44.
	
	The maximum value for the last track on the drive is stored in CH: 27 hexadecimal
	(39 decimal) if there are 40 tracks maximum, or 4Fh (79d) if there are 80
	tracks. The maximum sector number is stored in CL: 9h (9d), Fh (15d), 12h (18d),
	or 24h (36d). Finally, the maximum head number is stored in DH; because floppies
	have two heads, this is 1. (The ROM BIOS numbers heads and tracks, or cylinders,
	from 0, and sectors from 1.)
	
	Finally, DL indicates the number of floppy drives. Note that the value returned
	in DL (number of drives) is the number of floppy drives attached to the disk
	controller for the specified drive. Normally, there is only one controller, and
	thus DL=the total number of floppies. However, if floppies A and B are attached
	to different controllers, then DL=1 will be returned for each.
	
	So, from the previous example (values unrelated to the drive type are indicated
	by xx):
	
	AX=xxxx  BX=xx02  CX=4F0F  DX=0102  SP=xxxx  BP=xxxx  SI=xxxx  DI=xxxx
	DS=xxxx  ES=xxxx  SS=xxxx  CS=xxxx  IP=xxxx   xx xx xx xx xx xx xx NC
	xxxx:xxxx xxxx          xxx     xx
	
	NC, so no error; BL = 02, so 1.2 MB; CH=4F, or 80 tracks; CL=0F, or 15 sectors
	per track; DH=01, or 2 heads; DL=2, two drives. All of which indicates that
	there are two drives on this system, and this particular floppy drive is 1.2 MB.
	
	REFERENCES
	==========
	
	"IBM ROM BIOS Quick Reference," Ray Duncan. Microsoft Press. "QUE DOS
	Programmer's Reference," Terry Dettman. QUE Corporation.
	
	Additional query words: 6.22 3.x 4.x 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.x,4.x,5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
