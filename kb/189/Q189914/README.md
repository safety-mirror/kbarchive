---
layout: page
title: "Q189914: BUG: Wrapped CoolBar Control May GPF Client EXE Program"
permalink: /kb/189/Q189914/
---

## Q189914: BUG: Wrapped CoolBar Control May GPF Client EXE Program

{% raw %}

	Article: Q189914
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbDSupport
	Last Modified: 27-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 6.0, 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 6.0, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you wrap the CoolBar control inside a Visual Basic ActiveX Control, your
	Visual Basic client EXE may gave an Illegal Operation error when it shuts down.
	This occurs only on Windows 95, Windows 98, or Windows Me, and when the CoolBar
	control has child controls in a band. You will get the following error only in a
	compiled EXE and not in the Visual Basic IDE:
	
	  "This program has performed an illegal operation and will be shut down"
	
	RESOLUTION
	==========
	
	Clear all the bands from the CoolBar control before the client EXE shuts down.
	See Steps to Reproduce Behavior below for an example.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	To reproduce this behavior you must build an OCX that wraps the CoolBar control
	and a client EXE that uses that OCX. The EXE must be run on Windows 95, Windows
	98, or Windows Me. The EXE will not give the above error running on NT 4.0 or
	Windows 2000.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new ActiveX Control Project.
	
	2. Using the Projects menu, select Components to bring up the Components dialog
	  box. On the Controls Tab, check "Microsoft Windows Common Controls-3." Click
	  OK to close the Components window.
	
	3. Place a CoolBar on the UserControl.
	
	4. Change the name of the UserControl to "ctlCoolBar", and the project name to
	  "pjxCoolBar" (without the quotation marks).
	
	5. Place a TextBox, CommandButton, and ComboBox on the CoolBar control.
	
	6. Alternate mouse click on the CoolBar and select Properties from the pop-up
	  menu.
	
	7. On the Property Pages dialog box, select the Bands tab.
	
	8. For Index 1, set the Child property to Text1; for Index 2, set the Child
	  property to Command1; for Index 3, set the Child property to Combo1.
	
	9. Add the following code to the UserControl:
	
	        Public Sub ClearBands()
	           ' clearing all the bands before the control terminates
	           ' will keep the client EXE from having the Illegal Operation
	           ' error when it shuts down
	           CoolBar1.Bands.Clear
	        End Sub
	
	10. From the File menu, Save the project, and Make pjxCoolBar.OCX.
	
	11. Create a new Standard EXE Project. Form1 is created by default.
	
	12. Using the Projects menu, select Components to bring up the Components dialog
	  box. On the Controls tab, check PjxCoolBar. Click OK to close the dialog
	  window.
	
	13. Place the ctlCoolBar control on Form1.
	
	14. From the File menu, Save the project, and Make project1.exe.
	
	15. Run project1.exe and then shutdown project1.exe. You will get the Illegal
	  Operation error.
	
	16. To work around the error, add the following code to the Form's QueryUnload
	  event:
	
	        ctlCoolBar1.ClearBands
	
	17. Repeat steps 14 and 15. You will not get the error when you shut down
	  project1.exe.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrl kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : :5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
