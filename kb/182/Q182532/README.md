---
layout: page
title: "Q182532: HOWTO: DMA-Capable ATAPI Device Driver for Windows NT"
permalink: /kb/182/Q182532/
---

## Q182532: HOWTO: DMA-Capable ATAPI Device Driver for Windows NT

{% raw %}

	Article: Q182532
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Windows NT Service Pack 2 includes a new Windows NT device driver for direct
	memory access (DMA)-capable ATAPI devices. Using this new driver in Windows NT
	improves CPU utilization over standard PIO, increasing system usability while
	IDE operations are in progress.
	
	MORE INFORMATION
	================
	
	Using PCI bus master DMA, the CPU has to service only a single interrupt that is
	generated when the IDE command completes. This is compared to standard PIO,
	where the CPU has to service an interrupt from the device, every time a block of
	data becomes available to the host. Performance figures on a checked build
	showed approximately 20 to 30 percent CPU utilization using DMA, versus
	approximately 90 to 100 percent utilization during PIO transfers. Performance
	figures for DMA on a free build are even better, showing single-digit
	percentages in some cases.
	
	DMA Requirements
	----------------
	
	Registry keys must be added to enable direct memory access (DMA). The levels of
	DMA support include DMA detection level zero (disabled; this is the default) and
	DMA detection level one. The following criteria must be met before the driver
	will allow support for DMA detection level one:
	
	- PCI command register bit two (Master Enable) is set.
	
	- PCI device Class code is one.
	
	- PCI device Subclass code is one.
	
	- Programmer's interface bit seven is set.
	
	- Busmaster status register bits five and six are set. Bit 5 is set for the
	  master and bit 6 is set for the slave if the device exists. These bits should
	  be set by the BIOS, but many system BIOSs currently do not do this.
	
	Determining DMA Status
	----------------------
	
	Whether DMA is enabled can be determined by looking in the registry under:
	
	HKEY_LOCAL_MACHINE\HARDWARE\DEVICEMAP\Scsi\ScsiPort x
	
	  (where x represents the IDE channel; zero is the primary channel, one is the
	  secondary channel).
	
	Notice that the initiator ID is always 255 on IDE/ATAPI channels. There will be a
	DWORD value named DMAEnabled that will be set to zero if DMA is not active, and
	one, if DMA is active.
	
	Enabling DMA Detection Level 1
	------------------------------
	
	The ATAPI driver can be set to enable DMA use on a per-channel basis. Under the
	current SCSIPORT model, it is not possible to use DMA on one device and PIO on
	another if the devices are on the same channel.
	
	Enabling DMA use can be done by adding the following keys under:
	
	HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\atapi:
	\Parameters\DeviceX\ (where X represents the IDE channel)
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	When the keys have been created, you must create a DriverParameter STRING value
	and set it to DMADetectionLevel = 0x1.
	
	Disabling DMA Detection Level Zero
	----------------------------------
	
	The ATAPI driver can be set to disable DMA use on a per-channel basis. This can
	be done by adding the following keys under:
	
	HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\atapi:
	\Parameters\DeviceX\ (where X represents the IDE channel)
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	When you create the keys, you must also create a DriverParameter STRING value and
	set it to DMADetectionLevel = 0x0.
	
	Additional query words: DMA ATAPI IDE
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search
	Version           : winnt:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
