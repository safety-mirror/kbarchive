---
layout: page
title: "Q190670: HOWTO: Dynamically Add Controls to a Form with Visual Basic 6.0"
permalink: /kb/190/Q190670/
---

## Q190670: HOWTO: Dynamically Add Controls to a Form with Visual Basic 6.0

{% raw %}

	Article: Q190670
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbActiveX kbCtrlCreate kbVBp kbVBp600 kbFAQ kbVBp600FAQ
	Last Modified: 18-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Visual Basic 6.0 allows you to dynamically add control to a form at run- time
	using the new Add method of the Controls collection. This article shows how to
	dynamically add intrinsic and ActiveX controls.
	
	MORE INFORMATION
	================
	
	The following example dynamically adds two intrinsic and one ActiveX control to
	an application at run-time. The sample shows how to program the events of a
	dynamically added control. If you are dynamically adding a control that is not
	referenced in the project, you may need to add the control's License key to the
	Licenses collection. For more information on the Licenses collection, please see
	the REFERENCES section of this article.
	
	When you reference properties of the dynamically-added control, you must use the
	Object keyword to access the properties of the control. If you do not use the
	Object keyword, you will only be able to access the extender properties of the
	control.
	
	Attempting to access the extender properties without using the Object keyword
	causes the following 438 error:
	
	  "Object doesn't support this property or method."
	
	When an ActiveX control is dynamically added using the VBControlExtender object
	and WithEvents in the declare statement, you will need to use the ObjectEvent
	method to code all of the control's events. If you declare an intrinsic control
	WithEvents, you will get all the standard event methods for the type of control
	you declared. You can see this by adding the following declare statement in the
	Code window and then checking the Events dropdown for the declared variable in
	the Code window:
	
	  Dim WithEvents cmdMyCommand as VB.CommandButton
	
	Steps to Create Sample Project
	------------------------------
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. Add the following code to the code window of Form1:
	
	  Option Explicit
	  ' If you are adding an ActiveX control at run-time that is
	  ' not referenced in your project, you need to declare it
	  ' as VBControlExtender.
	  Dim WithEvents ctlDynamic As VBControlExtender
	  Dim WithEvents ctlText As VB.TextBox
	  Dim WithEvents ctlCommand As VB.CommandButton
	
	  Private Sub ctlCommand_Click()
	     ctlText.Text = "You Clicked the Command button"
	  End Sub
	
	  Private Sub ctlDynamic_ObjectEvent(Info As EventInfo)
	     ' test for the click event of the TreeView
	     If Info.Name = "Click" Then
	        ctlText.Text = "You clicked " & ctlDynamic.object.selecteditem.Text
	     End If
	  End Sub
	
	  Private Sub Form_Load()
	     Dim i As Integer
	     ' Add the license for the treeview to the license collection.
	     ' If the license is already in the collection you will get
	     ' the run-time error number 732.
	     Licenses.Add "MSComctlLib.TreeCtrl"
	
	     ' Dynamically add a TreeView control to the form.
	     ' If you want the control to be added to a different
	     ' container such as a Frame or PictureBox, you use the third
	     ' parameter of the Controls.Add to specify the container.
	     Set ctlDynamic = Controls.Add("MSComctlLib.TreeCtrl", _
	                      "myctl", Form1)
	     ' set the location and size of the control.
	     ctlDynamic.Move 1, 1, 2500, 3500
	
	     ' Add some nodes to the control.
	     For i = 1 To 10
	        ctlDynamic.object.nodes.Add Key:="Test" & Str(i), Text:="Test" _
	                                          & Str(i)
	        ctlDynamic.object.nodes.Add Relative:="Test" & Str(i), _
	                             Relationship:=4, Text:="TestChild" & Str(i)
	     Next i
	     
	     ' Make the control visible.
	     ctlDynamic.Visible = True
	
	     ' add a textbox
	     Set ctlText = Controls.Add("VB.TextBox", "ctlText1", Form1)
	     ' Set the location and size of the textbox
	     ctlText.Move (ctlDynamic.Left + ctlDynamic.Width + 50), _
	                   1, 2500, 100
	
	     ' Change the backcolor.
	     ctlText.BackColor = vbYellow
	
	     ' Make it visible
	     ctlText.Visible = True
	
	     ' Add a CommandButton.
	     Set ctlCommand = Controls.Add("VB.CommandButton", _
	                      "ctlCommand1", Form1)
	
	     ' Set the location and size of the CommandButton.
	     ctlCommand.Move (ctlDynamic.Left + ctlDynamic.Width + 50), _
	                      ctlText.Height + 50, 1500, 500
	
	     ' Set the caption
	     ctlCommand.Caption = "Click Me"
	
	     ' Make it visible
	     ctlCommand.Visible = True
	  End Sub
	
	3. Save and run the project. Try clicking the CommandButton and on different
	  Nodes in the TreeView. The TextBox will show what you click.
	
	(c) Microsoft Corporation 1998, All Rights Reserved.
	Contributions by Brian Combs, Microsoft Corporation
	
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	Q188577 HOWTO: What is the Licenses Collection Used For?
	
	Also search On-line Help for the following topics:
	
	- Add Method (Controls Collection)
	- Add Method (Licenses Collection)
	
	Additional query words: VBFAQProgramming runtime plugin
	
	======================================================================
	Keywords          : kbActiveX kbCtrlCreate kbVBp kbVBp600 kbFAQ kbVBp600FAQ 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
