---
layout: page
title: "Q91634: Using RAMDrive to Speed Up MS-DOS Task Swapper"
permalink: /kb/091/Q91634/
---

## Q91634: Using RAMDrive to Speed Up MS-DOS Task Swapper

{% raw %}

	Article: Q91634
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	RAMDrive is a memory-resident program that enables you to use part of your
	computer's random-access memory (RAM) as if it were a hard disk drive. By using
	RAMDrive, you can make MS-DOS Task Swapper run faster.
	
	When you install MS-DOS, the Setup program copies the RAMDRIVE.SYS file to your
	DOS directory. To create a RAM drive, you add a DEVICE= or DEVICEHIGH= command
	for RAMDRIVE.SYS to your CONFIG.SYS file.
	
	MORE INFORMATION
	================
	
	To speed up Task Swapper:
	
	1. Make a backup copy of your CONFIG.SYS file.
	
	2. Open your CONFIG.SYS file by using any text editor.
	
	3. Add a DEVICE= or DEVICEHIGH= command line for the RAMDRIVE.SYS device driver.
	  It should appear similar to the following:
	
	     device=c:\dos\ramdrive.sys 512 /e
	
	  This example creates a RAM drive that takes up 512K of extended memory. You
	  can specify how much and what type of memory your RAM drive uses by
	  customizing the command line. For more information about RAMDrive
	  command-line options, type "help ramdrive.sys" (without the quotation marks)
	  at the MS-DOS command prompt.
	
	4. Save the changes to your CONFIG.SYS file.
	
	5. Open your AUTOEXEC.BAT file.
	
	6. Set the TEMP environment variable to your RAM drive by adding a SET command
	  line. The drive letter of your RAM drive should be the letter after that of
	  the last disk drive in use. For example, if your last disk drive in use is C,
	  your RAM drive would be D. In this case, you would add the following command
	  to your AUTOEXEC.BAT file:
	
	     set temp=d:\
	
	7. Save the changes to your AUTOEXEC.BAT file.
	
	8. Restart your computer.
	
	NOTE: If RAMDrive is to use extended memory, your CONFIG.SYS file must contain a
	DEVICE= command for the HIMEM.SYS memory manager. If RAMDrive is to use expanded
	memory, your CONFIG.SYS file must contain a DEVICE command for the expanded
	memory manager that came with your memory board. The device command for RAMDrive
	must come after the one for the memory manager.
	
	You can improve the performance of RAMDrive by doing the following:
	
	- If you run programs from your RAM drive, list your RAM drive first in your
	  PATH= command. For example, if your RAM drive is drive E, add E:\ to the
	  beginning of the PATH= command.
	
	- If you use the EMM386 program as an expanded-memory emulator, do not put the
	  RAM drive in expanded memory. Although RAMDrive can also use this emulated
	  expanded memory, it won't be as efficient as it would if it were using real
	  physical memory.
	
	Additional query words: 6.22 6.0 ram drive 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
