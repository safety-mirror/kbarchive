---
layout: page
title: "Q226528: Streets &amp; Trips 2000 Err Msg: Failed to Initialize - Terminating"
permalink: /kb/226/Q226528/
---

## Q226528: Streets &amp; Trips 2000 Err Msg: Failed to Initialize - Terminating

{% raw %}

	Article: Q226528
	Product(s): Microsoft Automap
	Version(s): 
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsetup kbimu
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Expedia Streets and Trips 2000 
	- Microsoft MapPoint 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start one of the programs listed at the beginning of this article, you
	may receive either of the following error messages:
	
	   - Failed to open default template.
	
	   - Failed to initialize - terminating.
	
	When you click OK after you receive the second error message, you receive the
	following error message:
	
	  This program can no longer run. Click OK to acknowledge this message, and
	  then restart the program.
	
	When you click OK, you receive the following error message:
	
	  This program has performed an illegal operation and will be shut down.
	
	If you click Details, you receive the following error message:
	
	  Autmap71 caused an invalid page fault in module Autmap71.exe.
	
	CAUSE
	=====
	
	This behavior can occur for any of the following reasons:
	
	- The Autopins folder is missing, damaged, or named incorrectly.
	
	- The Pushpins folder is missing, damaged, or named incorrectly.
	
	- The Am7ppins.mdb file is missing or damaged.
	
	- The MDAC 2.1 Update installation was not completed successfully.
	
	RESOLUTION
	==========
	
	To resolve this issue, use the following methods in the order in which they are
	presented.
	
	NOTE: If you receive the following error message:
	
	  This program can no longer run. Click OK to acknowledge this message, and
	  then restart the program.
	
	Proceed directly to the "Download the Windows Libraries Update" method later in
	this article. If this method does not resolve the issue, use the following
	methods in the order in which they are presented.
	
	Remove the Program
	------------------
	
	To do this:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. Click Microsoft Expedia Streets and Trips 2000 or Microsoft MapPoint 2000,
	  and then click Add/Remove.
	
	4. Follow the instructions on the screen to remove the program. When you are
	  prompted to restart the computer, click Yes.
	
	Delete the Geography and Pushpins Folders
	-----------------------------------------
	
	To do this:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type the following line (including the quotation marks), and
	  then click OK:
	
	  "<drive>:\Program Files\Common Files\MicrosoftShared"
	
	  where <drive> is the drive letter of the hard disk on which Microsoft
	  Windows is installed.
	
	3. Right-click the Geography folder, and then click Delete. If you receive a
	  prompt to confirm the folder deletion, click Yes.
	
	4. Right-click the Pushpins folder, and then click Delete. If you receive a
	  prompt to confirm the folder deletion, click Yes.
	
	5. Close the Microsoft Shared window.
	
	
	Download the Windows Libraries Update
	-------------------------------------
	
	To download the Windows Libraries Update (Speu.exe):
	
	1. Visit the following Microsoft Web site:
	
	  http://www.microsoft.com/downloads/search.asp?
	
	2. In the Search By area, click Keywords.
	
	3. In the Operating System box, click the version of Microsoft Windows you are
	  using.
	
	4. In the Keywords box, type "microsoft libraries update" (without the quotation
	  marks), and then click Find It!
	
	5. In the list of found download files, click the Microsoft
	  Libraries Update link.
	
	6. On the Microsoft Libraries Update page, click Next.
	
	7. On the Microsoft Libraries Update: License Agreement page, click Next.
	
	8. Click "Save this program to disk", and then click OK.
	
	9. In the "Save in" box, click Desktop, and then click Save.
	
	Download the DCOM98 Update (Microsoft Windows 98 Only)
	------------------------------------------------------
	
	If you run Streets and Trips 2000 or MapPoint 2000 on a Windows 98-based
	computer, download the DCOM98 Update (Dcom98.exe) from the Microsoft Download
	Center. To do this:
	
	1. Connect to the following Microsoft Web site:
	
	  http://www.microsoft.com/downloads
	
	2. In the Search By box, click Keywords.
	
	3. In the Operating System box, click Windows 98.
	
	4. In the Keywords box, type "dcom" (without the quotation marks), and then
	  click Find It!
	
	5. In the list of found download files, click the "DCOM98 for Windows 98" link.
	
	6. Under Download Now, click the "DCOM98 for Windows 98" link.
	
	7. Click "Save this program to disk", and then click OK.
	
	8. In the "Save in" box, click Desktop, and then click Save.
	
	Download the DCOM95 Update (Microsoft Windows 95 Only)
	------------------------------------------------------
	
	If you run Streets and Trips 2000 or MapPoint 2000 on a Windows 95-based
	computer, download the DCOM95 Update (Dcom95.exe) from the Microsoft Download
	Center. To do this, follow these steps:
	
	1. Connect to the following Microsoft Web site:
	
	  http://www.microsoft.com/com/dcom/dcom95/download.asp
	
	2. Click the link next to the download site closest to you.
	
	3. Click "Save this program to disk", and then click OK.
	
	4. In the Save in box, click Desktop, and then click Save.
	
	Download and Install MDAC
	-------------------------
	
	Follow the steps for the operating system that is installed on your system.
	
	Windows 95:
	
	Install DCOM 95 first, and then follow the steps for Windows 98
	
	Windows 98/Millenium Edition:
	
	1. Connect to the following Microsoft Web site:
	
	  http://www.microsoft.com/downloads/release.asp?ReleaseID=23951
	
	2. Click the "MDAC_TYP.EXE - 7,882 Kb" link.
	
	3. Click "Save this program to disk", and then click OK.
	
	4. In the Save in box, click Desktop, and then click Save.
	
	5. Click Close when the copying process is done.
	
	To install the MDAC 2.5 SP1 update:
	
	1. Double-click the Mdac_typ.exe file on the Windows desktop.
	
	2. Follow the instructions on the screen to install the MDAC 2.5 sp1 update.
	
	3. When you receive the prompt to restart the computer, click Yes.
	
	If you encounter problems when you install the MDAC 2.5 sp1 update, restart the
	computer in Safe mode, and then repeat this procedure.
	
	Windows 2000:
	
	You need to install the Windows 2000 Service Pack 1. Doing so automatically
	installs the MDAC 2.5 SP1 and protects this MDAC release using System File
	Protection. This means that you can only remove MDAC 2.5 SP1 from Windows 2000
	by uninstalling the Windows 2000 Service Pack 1. You can download SP1 for
	Windows 2000 at the following website:
	
	  http://www.microsoft.com/windows2000/downloads/servicepacks/sp1/default.asp
	
	Clean Boot Your Computer
	------------------------
	
	To clean boot your computer, use the appropriate steps for your version of
	Microsoft Windows.
	
	Microsoft Windows 98:
	
	1. Click Start, point to Programs, point to Accessories, point to System Tools,
	  and then click System Information.
	
	2. On the Tools menu, click System Configuration Utility.
	
	3. On the General tab, click Selective Startup, and then click to clear the
	  following check boxes:
	
	   - Process Config.sys File
	   - Process Autoexec.bat File
	   - Process Winstart.bat File (if available)
	   - Process Win.ini File
	   - Load Startup Group Items
	
	4. Click OK. When you are prompted to restart the computer, do so.
	
	NOTE: To restore your original Startup options, click Normal Startup on the
	General tab in the System Configuration Utility tool.
	
	For additional information about how to clean boot Windows 98, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q192926 How to Perform Clean-Boot Troubleshooting for Windows 98
	
	
	Microsoft Windows 95:
	
	1. Restart the computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then select Step By Step Confirmation from the Startup menu.
	
	2. Press Y at each prompt except the following two prompts. At the following two
	  prompts, press N:
	
	   - Process your startup device driver (CONFIG.SYS) [Enter=Y, Esc=N]?
	   - Process your startup command file (AUTOEXEC.BAT) [Enter=Y,Esc=N]?
	
	3. Disable any anti-virus or disk tool programs installed on the computer. For
	  information about how to disable these programs, see the printed or online
	  documentation for the program.
	
	4. Quit all running programs except Explorer and Systray. To do this:
	
	  a. Press CTRL+ALT+DELETE.
	
	  b. Click the program you want to quit, and then click End Task.
	
	  c. If you receive a message that the program is busy or not responding, click
	     End Task again.
	
	  Repeat this step until you have quit all programs except Explorer and Systray.
	
	NOTE: To restore your original Startup options, restart the computer normally,
	and then enable any anti-virus or disk tool programs installed on the computer.
	For information about how to enable these programs, see the printed or online
	documentation for the program.
	
	For additional information about how to clean boot Windows 95, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q177604 Multimedia: Troubleshooting Using Clean Boot of Windows 95
	
	Install the Windows Libraries Update
	------------------------------------
	
	To do this:
	
	1. Double-click the Speu.exe file on the Windows desktop.
	
	2. Follow the instructions on the screen to install the Windows Libraries
	  Update.
	
	3. When you are prompted to restart the computer, click Restart Windows, and
	  then clean boot your computer.
	
	If you encounter problems installing the Windows Libraries Update, restart the
	computer in Safe mode, and then repeat these steps. For information about how to
	restart the computer in Safe mode, please see the "More Information" section of
	this article.
	
	Install the DCOM98 Update (Windows 98 Only)
	-------------------------------------------
	
	If you are using a Windows 98-based computer, you must install DCOM98 for Windows
	98 before you install MDAC 2.5. To install DCOM98 for Windows 98:
	
	1. Double-click the Dcom98.exe file on the Windows desktop.
	
	2. Follow the instructions on the screen to install DCOM98 for Windows 98.
	
	3. When you are prompted to restart the computer, click Restart Windows, and
	  then clean boot your computer.
	
	If you encounter problems installing DCOM98 for Windows 98, restart the computer
	in Safe mode, and then repeat these steps. For information about how to restart
	the computer in Safe mode, please see the "More Information" section of this
	article.
	
	Install the DCOM95 Update (Windows 95 Only)
	-------------------------------------------
	
	If you are using a Windows 95-based computer, you must install DCOM95 for Windows
	95 before you install MDAC 2.5. To install DCOM95 for Windows 95:
	
	1. Double-click the Dcom95.exe file on the Windows desktop.
	
	2. Follow the instructions on the screen to install DCOM95 for Windows 95.
	
	3. When you are prompted to restart the computer, click Restart Windows, and
	  then clean boot your computer.
	
	If you encounter problems installing DCOM95 for Windows 95, restart the computer
	in Safe mode, and then repeat these steps. For information about how to restart
	the computer in Safe mode, please see the "More Information" section of this
	article.
	
	Install the MDAC 2.5 Update
	---------------------------
	
	To do this:
	
	1. Double-click the Mdac_typ.exe file on the Windows desktop.
	
	2. Follow the instructions on the screen to install the MDAC 2.5 update.
	
	3. When you are prompted to restart the computer, click Restart Windows, and
	  then clean boot your computer.
	
	If you encounter problems installing the MDAC 2.5 Update, restart the computer in
	Safe mode, and then repeat these steps. For information about how to restart the
	computer in Safe mode, please see the "More Information" section of this
	article.
	
	NOTE: You may receive the following error message after you restart the
	computer:
	
	  Unable to open response file C:\Temp\Odbcconf.tmp.
	
	For additional information about this error message, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q218184 PRB: Restart After MDAC Installation Causes Error
	
	
	Reinstall the Program
	---------------------
	
	To do this:
	
	1. Insert the Expedia Streets and Trips 2000 CD-ROM or the MapPoint 2000 CD-ROM
	  into your CD-ROM drive.
	
	  If Setup does not start automatically:
	
	  a. Click Start, and then click Run.
	
	  b. In the Open box, type the following line, and then click OK:
	
	  <cd-rom>:\setup.exe
	
	     where <cd-rom> is the drive letter of your CD-ROM drive.
	
	2. Follow the instructions on the screen to install the program.
	
	3. When the installation process is complete, click OK, and then restart Windows
	  normally.
	
	
	
	MORE INFORMATION
	================
	
	To restart the computer in Safe mode, use the appropriate method for your
	version of Microsoft Windows:
	
	Windows 98
	----------
	
	1. Restart the computer, and then press and hold down the CTRL key until the
	  Microsoft Windows 98 Startup menu is displayed on the screen.
	
	2. On the Startup menu, select Safe Mode, and then press ENTER.
	
	3. When the computer starts in Safe mode, click OK.
	
	Windows 95
	----------
	
	1. Restart the computer, and then press the F8 key when the "Starting Windows
	  95" message is displayed on the screen.
	
	2. On the Startup menu, select Safe Mode , and then press ENTER.
	
	3. When the computer starts in Safe Mode, click OK.
	
	Additional query words: multi multi-media media mm gpf ipf auto-map amap
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsetup kbimu 
	Technology        : kbHomeProdSearch kbExpediaSearch kbMapptSearch kbMapPoint2000 kbExpediaStreets2000
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
