---
layout: page
title: "Q193400: BUG: Show Event in a UserControl Array Member Does Not Execute"
permalink: /kb/193/Q193400/
---

## Q193400: BUG: Show Event in a UserControl Array Member Does Not Execute

{% raw %}

	Article: Q193400
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A control array of UserControls is created in a Standard EXE project. When the
	Visible property of a member of the UserControl array is set to True, the Show
	Event does not execute.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a Standard EXE project in Visual Basic. Form1 is created default.
	
	2. Add an ActiveX Control project to the project group by completing the
	  following steps:
	
	  a. Select the File/Add project menu option to display the Add Project dialog
	     box.
	
	  b. In the New tab, select ActiveX Control.
	
	  c. Click Open to close the Add Project dialog box. UserControl1 is created by
	     default.
	
	3. Copy the following code in the Code window of UserControl1, and then close
	  all windows associated with UserControl1
	
	        Option Explicit
	
	        Private Sub UserControl_Hide()
	           Debug.Print "HIDE"
	        End Sub
	
	        Private Sub UserControl_Initialize()
	           Debug.Print "INIT"
	        End Sub
	
	        Private Sub UserControl_Show()
	           Debug.Print "SHOW"
	        End Sub
	
	4. Add an instance of UserControl1 to Form1. Set the Index property of
	  UserControl1 to 0.
	
	5. Add a CommandButton to Form1.
	
	6. Copy the following code to the Code window of Form1:
	
	        Option Explicit
	
	        Private Sub Command1_Click()
	           Load UserControl11(1)
	           UserControl11(1).Visible = True
	           UserControl11(1).Visible = False
	        End Sub
	
	7. Press the F8 key to step through each line of code until Form1 appears. After
	  Form1 appears, click the Command1 CommandButton and press the F8 key to step
	  through each event. Note that the Show event does not execute in response to
	  clicking the CommandButton. The expected behavior is for the Show event to
	  execute after the Initialize event.
	
	Additional query words: kbDSupport kbDSD kbVBp kbCtrl kbVBp600bug kbActiveX
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
