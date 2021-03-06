---
layout: page
title: "Q147276: MSB: How to Run Programs Via Multiple CD Changer"
permalink: /kb/147/Q147276/
---

## Q147276: MSB: How to Run Programs Via Multiple CD Changer

{% raw %}

	Article: Q147276
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Scholastic's Magic School Bus series: Explores the Human Body for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores Inside the Earth for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Ocean for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you have installed one of the products listed above from a multiple CD-ROM
	changer, you may have problems accessing the CD-ROM drive where the disk is
	located. This occurs when the disk is inserted in a drive different from the one
	from which the program was installed.
	
	RESOLUTION
	==========
	
	The program attempts to access and run from the CD-ROM drive you used for
	installation. If you want to run the program from a different CD-ROM drive, you
	must make a change to the drive designation in the Band.ini file for the
	program.
	
	To change the drive designation, use the instructions below for your version of
	Magic School Bus.
	
	MSB Human
	---------
	
	1. If you're using Windows 95/98, in Windows Explorer, open the MSKids\MSBHuman
	  folder.
	
	  If you're using Windows 3.x, in File Manager, open the MSKids\MSBHuman folder.
	
	2. Double-click the Band.ini file to open it in Notepad.
	
	3. You should see entries similar to the following:
	
	        [init]
	        main=!D:\msbhuman\ (where D: represents the CD-ROM drive)
	        second=!c:\mskids\msbhuman
	        user=&c:\mskids\msbhuman
	        syscaps=35
	
	        [info]
	        pid=25252-G90-8546345
	
	4. On the line where "D" represents the CD-ROM drive letter, change "D" to the
	  drive letter that matches where you have inserted the MSB Human Body compact
	  disc.
	
	  For example, if you have inserted the compact disc into drive G, change the
	  line from
	
	  main=!D:\msbhuman\
	
	  to
	
	  main=!G:\msbhuman\
	
	5. On the File menu, click Save.
	
	MSB Human Body should now function successfully in your multiple CD-ROM changer.
	
	MSB Ocean
	---------
	
	1. If you're using Windows 95/98, in Windows Explorer, open the
	  MSKids\MSBOcean\System folder.
	
	  If you're using Windows 3.x, in File Manager, open the MSKids\MSBOcean\System
	  folder.
	
	2. Double-click the Band.ini file to open it in Notepad.
	
	3. You should see entries similar to the following:
	
	        [init]
	        main=>C:\MSKids\MSBOcean\System\FC\;!C:\MSKids\MSBOcean\System\;!D:
	          \MSBOcean\;
	        user=>C:\MSKids\MSBOcean\System\ 
	        syscaps=2
	        minimize=1
	        [info]
	        pid=36506-442-2873026
	
	4. On the line where "D" represents the CD-ROM drive letter, change "D" to the
	  drive letter that matches where you have inserted the MSB Ocean compact
	  disc.
	
	  For example, if you have inserted the compact disc into drive G, change the
	  line from
	
	  main=>C:\MSKids\MSBOcean\System\FC\;!C:\MSKids\MSBOcean\System\;!D:
	  \MSBOcean\;
	
	  to
	
	  main=>C:\MSKids\MSBOcean\System\FC\;!C:\MSKids\MSBOcean\System\;!G:
	  \MSBOcean\;
	
	5. On the File menu, click Save.
	
	MSB Ocean should now run successfully in a multiple CD-ROM changer.
	
	MSB Inside the Earth
	--------------------
	
	To change the drive designation, use one of the methods listed below.
	
	Method 1, for Windows 95/98
	---------------------------
	
	1. If you're running Explores Inside the Earth, exit the program.
	
	2. Click Start, and then click Run.
	
	3. In the Open box, type "regedit" (without the quotation marks), and then click
	  OK.
	
	  WARNING: Using Registry Editor incorrectly can cause serious problems that may
	  require you to reinstall Windows. Microsoft cannot guarantee that problems
	  resulting from the incorrect use of Registry Editor can be resolved. Use
	  Registry Editor at your own risk.
	
	  For information about how to edit the registry, use the on-line Help in
	  Registry Editor, then go to the Changing Keys And Values Help topic. You
	  should make a backup copy of the registry files (System.dat and User.dat)
	  before you edit the registry.
	
	4. From the Registry menu, click Export Registry File.
	
	5. Type "Registry Backup" (without the quotation marks), then click "All" in the
	  Export Range area, and click Save.
	
	6. Locate and open the registry key shown below:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft Kids\MSB Earth\Init\ 
	
	7. Modify the "main" value, to access the appropriate drive.
	
	  For example, if you have inserted the compact disc into drive G, change the
	  line from:
	
	  main=>C:\MSKids\MSBEarth\System\FC\;!C:\MSKids\MSBEarth\System\;!D:
	  \MSBEarth\System\;
	
	  to
	
	  main=>C:\MSKids\MSBEarth\System\FC\;!C:\MSKids\MSBEarth\System\;!G:
	  \MSBEarth\System\;
	
	MSB Inside the Earth should now run successfully in a multiple CD-ROM changer.
	
	Method 2, for Windows 3.x
	-------------------------
	
	1. If you're using Windows 3.x, in File Manager, open the
	  \MSKids\MSBEarth\System.
	
	2. Double-click the Band.ini file to open it in Notepad.
	
	3. You should see entries similar to the following:
	
	        [init]
	        main=>C:\MSKids\MSBEarth\System\FC\;!C:\MSKids\MSBEarth\System\;!D:
	          \MSBEarth\System\;
	        user=>C:\MSKids\MSBEarth\System\User\ 
	        syscaps=3
	        minimize=1
	        cdaudio=1
	        miscellaneous=0
	        [info]
	        pid=37963-OEM-1208613-83643
	
	4. On the line where "D" represents the CD-ROM drive letter, change "D" to the
	  drive letter that matches where you have inserted the MSB Ocean compact
	  disc.
	
	  For example, if you have inserted the compact disc into drive G, change the
	  line from
	
	  main=>C:\MSKids\MSBEarth\System\FC\;!C:\MSKids\MSBEarth\System\;!D:
	  \MSBEarth\System\;
	
	  to
	
	  main=>C:\MSKids\MSBEarth\System\FC\;!C:\MSKids\MSBEarth\System\;!G:
	  \MSBEarth\System\;
	
	5. On the File menu, click Save.
	
	MSB Inside the Earth should now run successfully in a multiple CD-ROM changer.
	
	Additional query words: 1.00 kids mskids msb msbhb msbss frizz kbmm multimedia multi-media multi media multiple cdchanger cdrom cd winmsbhuman msbhuman
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbZNotKeyword kbKidsSearch kbScholasticHuman kbScholasticOcean kbScholasticEarth kbMSBSearch
	Version           : WINDOWS:1.0
	
	=============================================================================
	

{% endraw %}
