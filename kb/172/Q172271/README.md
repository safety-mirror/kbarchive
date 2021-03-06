---
layout: page
title: "Q172271: HOWTO: Change Case of a Control Name Within the Code Window"
permalink: /kb/172/Q172271/
---

## Q172271: HOWTO: Change Case of a Control Name Within the Code Window

{% raw %}

	Article: Q172271
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You might think that you could change the letter case of a control name by
	changing the value of the Name property of the control in the Property Browser,
	or by using the Edit/Replace feature to find and replace all instances of the
	control name. However, the first method does not work at all if you have
	existing code, and the second method does not work in all cases either. This
	article shows you how to use a combination of methods to accomplish the change.
	
	MORE INFORMATION
	================
	
	This article describes three methods to change the case of control references in
	code:
	
	- Rename the Control
	
	- Find and Replace
	
	- Temporarily Dimension a Variable
	
	Rename the Control
	------------------
	
	This method works only if you have made no references to the control in your
	code. Once you make any reference in code to a control, the editor remembers the
	control's name and case. Changing the case of the control name after this point
	does not affect existing or new code.
	
	Find and Replace
	----------------
	
	You can use the Edit/Replace feature to find and replace all instances of the
	control name with the new case.
	
	NOTE: This technique does not work in every case. When you add new event
	procedures, the old case is used. When combined with the next technique, you can
	change the case of all existing and new references to the control.
	
	Temporarily Dimension a Variable
	--------------------------------
	
	The editor is designed so that all references to a variable name use the same
	case as the statement in which the variable is dimensioned.
	
	For example, type the following inside a code window:
	
	     Dim MyVariable as string
	     myvariable = "hello"     ' is changed to MyVariable = "hello"
	
	To change the letter case of a variable, you must change its letter case within
	the dimension statement. In the previous example, to change MyVariable to
	Myvariable, alter the first line to:
	
	     Dim Myvariable as String
	
	You can take advantage of this feature to change the letter case of a control's
	name. Just dimension a variable of the desired name and case. After you press
	ENTER, the case will change throughout the code window. Then simply delete the
	unnecessary dimension statement.
	
	NOTE: This technique does not work in every case. It does not change the name of
	existing event procedure names because they are a compound name. However, new
	event procedure names will reflect the new case. When combined with the previous
	technique, you can change the case of all existing and new references to the
	control.
	
	Example
	-------
	
	The following steps show how to change the case of Command1 to command1 by using
	a combination of the second and third techniques:
	
	1. Start a new project in Visual Basic and add a command button (Command1) to
	  the default form.
	
	2. Add the following line of code to the Command1_Click Event:
	
	        Command1.Caption = "hello"
	
	3. Change the name property of the command button from Command1 to command1.
	  Note the code has not changed case.
	
	4. Add the following line of code to the Command1_Click event and press ENTER:
	
	        Dim command1 as string
	
	5. Note the case of the Command.Caption reference has been changed. However, the
	  case of the event procedure name, Command1_Click, has not.
	
	6. Delete the line added in step 4. The change will remain in effect until
	  another variable is dimensioned with a different case. If you leave the line
	  in the program, you will receive an error when the program is compiled.
	
	7. Add a new event procedure, Command_GotFocus. Note that the new event
	  procedure reflects the new case.
	
	8. You can change the case of existing event procedures manually, or you can use
	  the Edit/Replace dialog box to search for "Sub Command1_" and replace it with
	  "Sub command1_".
	
	Additional query words: kbdse kbDSupport kbVBp kbVBp500 kbVBp600 kbVBp400 kbCtrl
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0,6.0
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
