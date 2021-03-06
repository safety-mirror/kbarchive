---
layout: page
title: "Q189412: ODE97: &quot;Always Overwrite&quot; Option Fails When MDB Is in WinPath"
permalink: /kb/189/Q189412/
---

## Q189412: ODE97: &quot;Always Overwrite&quot; Option Fails When MDB Is in WinPath

{% raw %}

	Article: Q189412
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 16-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Access 97 
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	Advanced: Requires expert coding, interoperability, and multiuser skills.
	
	SYMPTOMS
	========
	
	When you use the Microsoft Office Developer Edition Tools to distribute a custom
	application and the destination folder for the application file is set to
	$WinPath, the Always Overwite option fails when you try to install a modified
	version of the application file.
	
	RESOLUTION
	==========
	
	To resolve this problem, select $AppPath as the destination folder for the main
	application file.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Access 97.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start Microsoft Access and open the sample database Northwind.mdb.
	
	2. On the Tools menu, click Startup.
	
	3. In the Startup dialog box, click the arrow in the Display Form box, select
	  Main Swichboard, and then click OK.
	
	4. Close the sample database Northwind.mdb.
	
	5. Run the ODE Setup Wizard.
	
	6. On the first screen of the wizard, click to select "Create a new set of setup
	  options for my application's custom setup program", and then click Next.
	
	7. On the next screen of the wizard, add the sample database Northwind.mdb to
	  the List Of Files box.
	
	8. Click the arrow in the Destination Folder box, and select $(WinPath). Click
	  the arrow in the Overwrite Existing box, and select Always.
	
	9. Click to select "Set as Application's main file", and then click Next six
	  times to move to final screen of the Setup Wizard.
	
	10. Click to select "Network or CD Setup", and then click Finish.
	
	11. Click Yes to save the template, and then click Save.
	
	12. Install the application that you just created.
	
	13. Start Microsoft Access, and open the sample database Northwind.mdb.
	
	14. Open the Main SwitchBoard form in Design view.
	
	15. On the View menu, click Properties, and then click the All tab.
	
	16. Modify the Caption property to read as follows:
	
	  Main Switchboard Version 2.0
	
	17. Close and save the form.
	
	18. Close the database, and run the ODE Setup Wizard.
	
	19. On the initial screen of the setup wizard, click to select the "Use
	  previously saved setup options..." check box, and then click Next.
	
	20. Click Open to open the template that you saved in step 11.
	
	21. Click Next four times.
	
	22. Increase the version number of the application, and click Finish to complete
	  the Setup Wizard.
	
	23. When you are asked if you would like to overwrite the setup files, click
	  Yes.
	
	24. When asked if you would like to save the current Setup template, click No.
	
	Note that after you re-install the custom application, the copy of Northwind
	residing in the $(WinPath) folder is not the modified copy, but the original.
	
	Additional query words: prb
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbOfficeSearch kbAudDeveloper kbAccessSearch kbAccess97 kbOffice97Search kbAccess97Search kbOffice97 kbOffice97DevSearch
	Version           : WINDOWS:97
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
