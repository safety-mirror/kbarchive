---
layout: page
title: "Q178495: FIX: Invalid Page Fault When Deleting Nodes in TreeView Control"
permalink: /kb/178/Q178495/
---

## Q178495: FIX: Invalid Page Fault When Deleting Nodes in TreeView Control

{% raw %}

	Article: Q178495
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,97,97sp1,97sp2,97sp3
	Operating System(s): 
	Keyword(s): kbAPI kbVBp kbVBp500bug kbVBp600fix kbVS97sp1 kbVS97sp2 kbVS97sp3 kbGrpDSVB _IK kbContr
	Last Modified: 18-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	While attempting to delete nodes from a TreeView control, you receive an Invalid
	Page Fault and your Visual Basic application is terminated.
	
	CAUSE
	=====
	
	This problem may occur when the user clicks on the TreeView control and this
	action causes an event procedure to run that attempts to delete nodes from the
	TreeView before the TreeView gets the focus.
	
	RESOLUTION
	==========
	
	To correct this problem, call the DoEvents function in the MouseDown event of
	the TreeView Control. For example:
	
	     Private Sub TreeView1_MouseDown(Button As Integer, Shift As Integer, _
	       x As Single, y As Single)
	          DoEvents
	     End Sub
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Basic 6.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Click Components from the Project menu and check Microsoft Windows Common
	  Controls 5.0.
	
	3. Place a TreeView control and a TextBox control on Form1.
	
	4. Copy the following code to the Code window of Form1:
	
	        Private Sub Form_Load()
	           TreeView1.Nodes.Add , , "A", "A"
	        End Sub
	
	        Private Sub Text1_LostFocus()
	           TreeView1.Nodes.Clear
	        End Sub
	
	5. On the Run menu, click Start, or press the F5 key to start the program.
	
	6. Click on the TextBox so that it has the focus.
	
	7. Click on the "A" node in the TreeView control.
	
	  On Windows 95, Windows 98, or Windows Me, you receive the following error:
	
	  VB5 caused an invalid page fault in module COMCTL32.DLL at <address>.
	
	  On Windows NT, you receive the following error:
	
	  Exception: Stack overflow in VB5.EXE
	
	  -or-
	
	  The exception unknown software exception (0xc00000fd) occurred in the
	  application at location <address>.
	
	  NOTE: You may have to repeat steps 6 and 7 several times before seeing the
	  problem.
	
	
	Additional query words: application error crash gpf ipf page fault
	
	======================================================================
	Keywords          : kbAPI kbVBp kbVBp500bug kbVBp600fix kbVS97sp1 kbVS97sp2 kbVS97sp3 kbGrpDSVB _IK kbControl 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB500
	Version           : :5.0,97,97sp1,97sp2,97sp3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
