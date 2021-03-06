---
layout: page
title: "Q149783: INFO: ISAM Settings and Jet 3.0"
permalink: /kb/149/Q149783/
---

## Q149783: INFO: ISAM Settings and Jet 3.0

{% raw %}

	Article: Q149783
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbRegistry kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With the 16-bit version of Visual Basic 4.0, the IniPath property of the
	DBEngine object could be set to an application's .ini file. With the 32-bit Jet
	engine, setting the IniPath property of the DBEngine object to
	"C:\Windows\MyApp.INI" does not load the Paradox ISAM settings.
	
	STATUS
	======
	
	This behavior is by design. The 32-bit Jet engine retrieves its settings from
	the registry.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. To use the ISAM settings with the 16-bit Jet engine, place the following code
	  in the Load Event for the project:
	
	        DBEngine.IniPath = "C:\Windows\MyApp.INI"
	
	  where the following appears in the MyApp.INI file:
	
	        [Paradox ISAM]
	        ParadoxNetStyle=4.X
	        ParadoxNetPath=F:\ 
	        ParadoxUserName=JoeUser
	
	2. To place the Paradox ISAM settings into the Registry under
	  "HKEY_CURRENT_USER\Software\VB and VBA Program Settings," use the following
	  code:
	
	      SaveSetting "AppName", "Engines\Paradox", "ParadoxNetStyle", "4.X"
	      SaveSetting "AppName", "Engines\Paradox", "ParadoxNetPath", "F:\"
	      SaveSetting "AppName", "Engines\Paradox", "ParadoxUserName", _
	      "JoeUser"
	
	3. To obtain the ISAM settings from the Registry, place the following code in
	  the Load Event:
	
	        DBEngine.IniPath = _
	           "HKEY_CURRENT_USER\Software\VB and VBA Program Settings\AppName"
	
	REFERENCES
	==========
	
	For more information on Paradox Registry setting, please refer to the following
	book:
	
	"Jet Database Engine Programmer's Guide" published by Microsoft Press.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbRegistry kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
