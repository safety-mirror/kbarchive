---
layout: page
title: "Q87980: SYSTEM.INI Entries Made by PC-Speaker Explained"
permalink: /kb/087/Q87980/
---

## Q87980: SYSTEM.INI Entries Made by PC-Speaker Explained

{% raw %}

	Article: Q87980
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses the entries that the PC-Speaker driver for Microsoft
	Windows version 3.1 makes in the SYSTEM.INI and what they mean. The following
	are the default entries:
	
	     [drivers]
	     Wave=speaker.drv
	
	     [Speaker.drv]
	     CpuSpeed=28
	     Volume=500
	     Version=774
	     Enhanced=1
	     MaxSeconds=3
	     LeaveInterruptsEnabled=0
	
	MORE INFORMATION
	================
	
	NOTE: This driver can be manually installed into Windows. Query on the following
	here in the Microsoft Knowledge Base for more information:
	
	  pc-speaker and driver and setup and initializes
	
	CpuSpeed
	--------
	
	This indicates the setting for speaker speed (5-300). Changing this setting slows
	down or speeds up the play back of the wave file, and is similar to setting the
	speeds on a record turntable. This setting can be changed by doing the
	following:
	
	1. Run Control Panel.
	
	2. Choose the Drivers icon, and select the Wave Driver For PC-Speaker driver.
	
	3. Make any necessary changes and then choose OK.
	
	Volume
	------
	
	This indicates the volume level for the speaker. This setting can be adjusted
	through the Control Panel as described above.
	
	Version
	-------
	
	This indicates the version number of the speaker driver.
	
	Enhanced
	--------
	
	This indicates whether Windows is running in 386 enhanced mode or not. The value
	is changed when Windows is run in 386 enhanced mode (1), or in standard mode
	(0).
	
	MaxSeconds
	----------
	
	This indicates the maximum number of seconds a wave file will play (1-10, none).
	When set to "none" the maximum becomes a combination of the wave file size and
	system memory. This setting can be adjusted through the Control Panel as
	described above.
	
	LeaveInterruptsEnabled
	----------------------
	
	When this is set to 1, it allows the mouse and other interrupt sensitive devices
	to function while a wave file is playing. If left at the default, 0, it will not
	allow these devices to function. This setting can be adjusted through the
	Control Panel as described above.
	
	The PC-Speaker driver is available on the Microsoft Download Service by dialing
	(425) 936-6735. The file is SPEAK.EXE.
	
	Additional query words: 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
