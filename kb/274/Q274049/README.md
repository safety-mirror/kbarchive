---
layout: page
title: "Q274049: Encarta: Recording Problems When Two Sound Cards Are Installed"
permalink: /kb/274/Q274049/
---

## Q274049: Encarta: Recording Problems When Two Sound Cards Are Installed

{% raw %}

	Article: Q274049
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 
	Operating System(s): 
	Keyword(s): kbenv kbsound kbimu
	Last Modified: 23-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta Encyclopedia Deluxe 2001 for Windows 
	- Microsoft Encarta Encyclopedia Standard 2001 for Windows 
	- Microsoft Encarta Language Learning French 
	- Microsoft Encarta Language Learning French Deluxe 
	- Microsoft Encarta Language Learning Spanish 
	- Microsoft Encarta Language Learning Spanish Deluxe 
	- Microsoft Encarta Reference Suite 2001 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use one of the Encarta programs listed at the beginning of this
	article, you may be unable to use the Text-to-Speech or the Voice Control
	feature in Microsoft Encarta Encyclopedia or record sounds properly in the
	Microsoft Encarta Language Learning programs.
	
	In addition, you may receive error messages stating that your sound card is not
	configured properly.
	
	NOTE: The sound recording function in Microsoft Windows may still work properly.
	
	CAUSE
	=====
	
	This behavior can occur if more than one sound card is installed in your
	computer.
	
	The recording software that is installed with Encarta Encyclopedia and the
	Encarta Language Learning programs is associated with a particular sound device.
	If more than one sound device is installed in the computer, the Encarta program
	may not be associated with the sound device that is associated with sound
	recording and playback in Windows.
	
	RESOLUTION
	==========
	
	To resolve this issue, temporarily disable the sound device that the Encarta
	program is associated with, and then uninstall and reinstall the Encarta
	program.
	
	To do this, use the following methods in the order in which they are presented.
	
	Temporarily Disable the Conflicting Sound Device
	------------------------------------------------
	
	To temporarily disable the conflicting sound device:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Multimedia or "Sound and Multimedia".
	
	3. On the Audio tab, note the sound device that is listed in the "Preferred
	  device" box in the Recording or Sound Recording section.
	
	4. Click the Devices or the Advanced tab. If you are using Microsoft Windows
	  2000, click the Hardware tab.
	
	5. Locate the sound device that is associated with the Encarta program. To do
	  this, use the appropriate method for your operating system.
	
	  Microsoft Windows 95 and Microsoft Windows 98:
	
	  1. Click the plus sign (+) next to Audio Devices.
	
	  2. Double-click the sound device that is not listed in the "Preferred device"
	     box on the Audio tab.
	
	  Microsoft Windows Millennium Edition:
	
	  1. Click the plus sign (+) next to Audio Devices.
	
	  2. Double-click the sound device that is not listed in the "Preferred device"
	     box on the Audio tab.
	
	  Microsoft Windows 2000:
	
	  Double-click the sound device that is not listed in the "Preferred device" box
	  on the Audio tab.
	
	6. Disable the sound device that you identified in step 5. To do this, use the
	  appropriate method for your operating system.
	
	  Windows 95 and Windows 98:
	
	  Click "Do not use audio features on this device", and click OK.
	
	  Windows Millennium Edition:
	
	  Click "Do not use audio features on this device", and click OK.
	
	  Windows 2000:
	
	  On the General tab,click "Do not use this device (disabled)" in the "Device
	  usage box", and then click OK.
	
	7. Click OK, and then close all open windows on the desktop.
	
	Uninstall and Reinstall the Encarta Program
	-------------------------------------------
	
	To do this, use the appropriate steps for your operating system.
	
	Windows 95 and Windows 98:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. On the Install/Uninstall tab, click the Encarta program that you want to
	  uninstall, and then click Add/Remove.
	
	4. Follow the instructions on the screen to uninstall the program. If you are
	  prompted to restart the computer, do so.
	
	5. Insert the installation CD-ROM for the Encarta program into the CD-ROM drive.
	  Follow the instructions on the screen to reinstall the Encarta program.
	
	Windows Millennium Edition:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. On the Install/Uninstall tab, click the Encarta program that you want to
	  uninstall, and then click Add/Remove.
	
	4. Follow the instructions on the screen to uninstall the program. If you are
	  prompted to restart the computer, do so.
	
	5. Insert the installation CD-ROM for the Encarta program into the CD-ROM drive.
	  Follow the instructions on the screen to reinstall the Encarta program.
	
	Windows 2000:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. In the list of currently installed programs, click the Encarta program that
	  you want to uninstall, and then click Remove.
	
	4. Follow the instructions on the screen to uninstall the program. If you are
	  prompted to restart the computer, do so.
	
	5. Insert the installation CD-ROM for the Encarta program into the CD-ROM drive.
	  Follow the instructions on the screen to reinstall the Encarta program.
	
	When you reinstall the Encarta program and verify that you are able to record
	sounds properly in the program, you can re-enable the additional sound device
	without creating a device conflict.
	
	Additional query words: multi multi-media media mm ellf ells ee2001 audio records cannot
	
	======================================================================
	Keywords          : kbenv kbsound kbimu 
	Technology        : kbHomeProdSearch kbHomeMMsearch kbEncartaSearch kbHLangSpanish kbEncartaEncycSearch kbHLangFrench kbEncartaReference2001
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
