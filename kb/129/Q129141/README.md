---
layout: page
title: "Q129141: Available Diagnostics for Digiboard C/CON 16 While Operational"
permalink: /kb/129/Q129141/
---

## Q129141: Available Diagnostics for Digiboard C/CON 16 While Operational

{% raw %}

	Article: Q129141
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.11 3.5 3.51 4.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbinterop
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft LAN Manager, version 2.2c 
	- Microsoft Windows for Workgroups version 3.11 
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information discusses tools and procedures available for
	diagnosing and troubleshooting problems with the Digiboard C/CON 16 while the
	device is operational.
	
	The C/CON 16 control panel (located in the front of the device) contains 10 LED
	indicators, a 2 digit LED display, and two buttons that are useful in diagnosing
	and monitoring problems and functions of the concentrator.
	
	The following is a visual description of the Digiboard C/CON 16 control panel:
	
	--------------------------------------------------------------------------
	|                                                                        |
	|                     TD RD RTS CTS DSR DCD DTR RI OFC IFC  ------       |
	|DigiChannel C/CON-16 () () ()  ()  ()  ()  ()  () ()  ()   | AC |  < >  |
	|                        0%                       100%      ------       |
	|                                                                        |
	
	MORE INFORMATION
	================
	
	The push buttons at the right of the control panel are used to access twenty
	display modes, by pushing the left or right arrow buttons.
	
	The table below describes these modes in detail.
	
	When AC (activity) is shown on the 2 digit LED, the ten LEDs flash from left to
	right. The speed of this strobing effect indicates the overall activity of the
	device.
	
	1-16 shows the channels from 1 through 16. Under these modes, the LEDs act the
	same as a line monitor.
	
	NOTE: If the push buttons are pressed simultaneously, software flow control is
	turned off.
	
	PC displays the Packet Count on the LEDs as a binary count of total packet count
	that are received or transmitted. The low byte is the left most LED (TD).
	
	EC displays the Error Count (total errors) in binary. Pressing both push buttons
	at once resets the count to zero.
	
	PU describes the Process Utilization. The LEDs are used as a bar graph showing
	the concentrator's processor time in percentage. From the left, each LED
	increments the PU by 10 percent.
	
	LU describes the Line Utilization. The LEDs are used as a bar graph showing the
	concentrator's processor time in percentage. From the left, each LED increments
	the PU by 10 percent.
	
	1n, 2n, 3n, 4n, 5n, 6n, 7n, and 8n show the node number of the concentrator. The
	LEDs function just as they do in AC mode.
	
	Digiboard is manufactured by Digi International, Inc., a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding these products'
	performance or reliability.
	
	Additional query words: prodnt pushbuttons wfw wfwg
	
	======================================================================
	Keywords          : kb3rdparty kbinterop 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbAudDeveloper kbWinNT310Search kbWinNTW310Search kbLanManSearch kbWFWSearch kbWFW311 kbLanMan220c
	Version           : 3.1 3.11 3.5 3.51 4.0
	
	=============================================================================
	

{% endraw %}
