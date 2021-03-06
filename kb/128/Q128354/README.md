---
layout: page
title: "Q128354: Hang or &quot;Read Fault&quot; Accessing Bad Cluster on Compressed Drive"
permalink: /kb/128/Q128354/
---

## Q128354: Hang or &quot;Read Fault&quot; Accessing Bad Cluster on Compressed Drive

{% raw %}

	Article: Q128354
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:95
	Operating System(s): 
	Keyword(s): msdos diskmem win95 kbDiskMemory
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using a real-mode driver (DRVSPACE.BIN or DBLSPACE.BIN) and you try
	to access a file on a DriveSpace or DoubleSpace compressed drive, the computer
	stops responding (hangs).
	
	If you are using a protected-mode driver (DRVSPACX.VXD), you receive the error
	message "Read Fault."
	
	To determine whether you are using a real-mode or protected-mode driver, run
	DRVSPACE.EXE and click About DriveSpace on the Help menu.
	
	CAUSE
	=====
	
	The file that you are trying to access is stored in one or more bad clusters. A
	bad cluster on a compressed drive is a cluster that cannot be read successfully.
	Note that an unreadable cluster on a compressed drive does not always indicate a
	media defect on the physical surface of the disk.
	
	RESOLUTION
	==========
	
	With the protected-mode DriveSpace driver loaded, run ScanDisk for Windows and
	click the Thorough option button in the Type Of Test box. Test both the system
	and data areas on the compressed drive, as well as on the host drive. To run
	ScanDisk and perform a thorough test, follow these steps:
	
	1. Click the Start button, point to Programs, point to Accessories, point to
	  System Tools, then click ScanDisk.
	
	2. Click the drives you want to test (you should test both the compressed drive
	  and the host drive).
	
	3. In the Type Of Test box, click the Thorough option button.
	
	4. Click the Options button.
	
	5. Click the System And Data Areas option button.
	
	6. Click the OK button.
	
	7. Click the Start button.
	
	
	MORE INFORMATION
	================
	
	Bad cluster markings due to physical media defects should appear only on
	uncompressed drives. If ScanDisk is unable to read a cluster on a DriveSpace
	compressed drive, ScanDisk erases the Microsoft DriveSpace FAT (MDFAT) entry for
	that cluster and changes the portion of the file that was using the cluster to 0
	bytes in length. The physical sectors previously used by the unreadable cluster
	are marked as free and can be used again.
	
	Additional query words: 6.00 6.20 6.21 6.22
	
	======================================================================
	Keywords          : msdos diskmem win95 kbDiskMemory 
	Technology        : kbWin95search kbZNotKeyword3 kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:95
	
	=============================================================================
	

{% endraw %}
