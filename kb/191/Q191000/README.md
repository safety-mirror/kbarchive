---
layout: page
title: "Q191000: BUG: Unexpected Error Entering Break Mode in Shared Module"
permalink: /kb/191/Q191000/
---

## Q191000: BUG: Unexpected Error Entering Break Mode in Shared Module

{% raw %}

	Article: Q191000
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When sharing code modules between projects that run in the IDE at the same time,
	an unexpected error occurs if one project has the shared module open while the
	other project enters break mode in the same module. The error message received
	is:
	
	  The copy of this file which might have changes is already opened.
	
	Clicking OK on this message causes "Unexpected Error (59999)" to occur.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	Create a Shared Module:
	
	1. Create a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Add a CommandButton to Form1, and paste the following code into the Form1
	  code window:
	
	        Private Sub Command1_Click()
	           Module1.SharedCode
	        End Sub
	
	3. On the Project menu, click Add Module. Module1 is added to the project.
	
	4. Paste the following code into Module1:
	
	        Public Sub SharedCode()
	           Debug.Print "Shared Code"
	        End Sub
	
	5. Click the insertion point on the Debug.Print line, and then press the F9 key
	  to toggle the breakpoint on.
	
	6. Save the module as Module1, and close its code window.
	
	Add the Shared Module to Another Project:
	
	1. On the File menu, click Add Project. Select ActiveX Control, and then click
	  Open. UserControl1 is created by default.
	
	2. Add Module1 to Project2.
	
	3. Place a CommandButton on UserControl1 in Project2, and then paste the
	  following code into the UserControl1 code window:
	
	        Private Sub Command1_Click()
	           Module1.SharedCode
	        End Sub
	
	4. Open Module1 in Project2, and repeat step 5 to place a breakpoint on the
	  Debug.Print line.
	
	5. Close the design window of UserControl1, and place it on Form1 of Project1 so
	  the CommandButtons on both are visible.
	
	Run Both Projects with the Shared Module:
	
	1. Press the F5 key to run Project1. Click Command1 on UserControl1.
	
	2. Press the F5 key at the breakpoint.
	
	3. Click Command1 on Form1.
	
	RESULTS: The IDE attempts to open Form1's instance of the shared module
	(Module1), and you receive the following error message:
	
	  The copy of this file which might have changes is already opened.
	
	Clicking OK on this message causes "Unexpected Error (59999)" to occur.
	
	Additional query words: kbVBp500bug kbVBp600bug kbide kbdss kbDSupport kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
