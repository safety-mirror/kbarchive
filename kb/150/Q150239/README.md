---
layout: page
title: "Q150239: PRB: Option Button TabStop Property Is Set to True at Run-time"
permalink: /kb/150/Q150239/
---

## Q150239: PRB: Option Button TabStop Property Is Set to True at Run-time

{% raw %}

	Article: Q150239
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp400 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Microsoft Visual Basic program contains an Option button that is set to True
	at runtime. However, the program is designed so a user cannot get to the Option
	Button by using the Tab key. For this condition to occur, the TabStop property
	of the Option button is set to False and the Value property is set to True at
	design time. When running the program, you can tab to the Option button.
	
	CAUSE
	=====
	
	The TabStop property is changed to True at run-time.
	
	WORKAROUND
	==========
	
	Set the TabStop property to False in the LostFocus event of each option button.
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: 4.00 vb4win vb4all
	
	======================================================================
	Keywords          : kbCtrl kbVBp400 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
