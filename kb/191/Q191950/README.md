---
layout: page
title: "Q191950: HOWTO: Control Microsoft Agent with Visual FoxPro"
permalink: /kb/191/Q191950/
---

## Q191950: HOWTO: Control Microsoft Agent with Visual FoxPro

{% raw %}

	Article: Q191950
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbvfp300 kbvfp500 kbvfp600 kbGrpDSFox kbDSupport
	Last Modified: 24-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Agent is a set of programmable software services that supports the
	presentation of interactive animated characters within the Microsoft Windows
	interface. Developers can use characters as interactive assistants to introduce,
	guide, entertain, or otherwise enhance applications in addition to the
	conventional use of windows, menus, and controls. Microsoft Agent could be used,
	for instance, as a data validation alert, or even as a number reader for
	heads-down data entry. This article demonstrates how to use Microsoft Agent from
	within Visual FoxPro.
	
	MORE INFORMATION
	================
	
	In order to use the sample code in this article, you need to install the
	Microsoft Agent core components. Use one of the following methods to obtain
	Microsoft Agent:
	
	- Download the Microsoft Agent core components from the following URL:
	
	  http://www.msdn.microsoft.com/msagent/agentdl.asp
	
	-or-
	
	- Microsoft Agent can be installed from the Visual Studio 6.0 Disk 3. The files
	  are located in the following folder:
	
	  Common\Tools\Vb\Msagent
	
	After you download and install the core components, download the Genie character
	data from the following URL:
	
	  http://www.msdn.microsoft.com/msagent/characterdata.asp
	
	The following sample code demonstrates several methods used to control a
	Microsoft Agent character.
	
	Sample Code
	-----------
	
	     *-- Code begins here.
	     PUBLIC oGenie, oAgent
	
	     *-- Initialize the Agent object, which then allows us to
	     *-- load and use characters.
	     oAgent = createobject("Agent.Control.1")
	     oAgent.connected = .t.
	
	     *-- Load a character from the character definition.
	     *-- Modify the path to point to where the character
	     *-- definition is installed.
	     oAgent.characters.load("Genie", ;
	       "\program files\microsoft agent\characters\genie.acs")
	
	     *-- Create the character object, the Genie in this example.
	     oGenie = oAgent.characters("Genie")
	     oGenie.Show
	     Control = CREATEOBJECT("Form1")
	     Control.Show
	     READ EVENTS
	
	     **************************************************
	     *-- Form:         form1
	     *-- ParentClass:  form
	     *-- BaseClass:    form
	     *
	     DEFINE CLASS form1 AS form
	
	        Top = 31
	        Left = 80
	        Height = 279
	        Width = 368
	        DoCreate = .T.
	        Caption = "Agent Control"
	        Name = "Form1"
	
	        ADD OBJECT text1 AS textbox WITH ;
	           Height = 25, ;
	           Left = 11, ;
	           Top = 30, ;
	           Width = 337, ;
	           Name = "Text1"
	
	        ADD OBJECT command1 AS commandbutton WITH ;
	           Top = 72, ;
	           Left = 12, ;
	           Height = 37, ;
	           Width = 96, ;
	           Caption = "Speak", ;
	           Name = "Command1"
	
	        ADD OBJECT label1 AS label WITH ;
	           Caption = "Enter text below:", ;
	           Height = 25, ;
	           Left = 11, ;
	           Top = 6, ;
	           Width = 120, ;
	           Name = "Label1"
	
	        ADD OBJECT cmdmove AS commandbutton WITH ;
	           Top = 228, ;
	           Left = 36, ;
	           Height = 37, ;
	           Width = 84, ;
	           Caption = "Move", ;
	           Name = "cmdMove"
	
	        ADD OBJECT spntop AS spinner WITH ;
	           Height = 24, ;
	           Left = 97, ;
	           Top = 132, ;
	           Width = 60, ;
	           Value = 50, ;
	           Name = "spnTop"
	
	        ADD OBJECT label2 AS label WITH ;
	           Caption = "Position Top", ;
	           Height = 25, ;
	           Left = 12, ;
	           Top = 132, ;
	           Width = 72, ;
	           Name = "Label2"
	
	        ADD OBJECT label3 AS label WITH ;
	           Caption = "Move Speed", ;
	           Height = 25, ;
	           Left = 12, ;
	           Top = 192, ;
	           Width = 72, ;
	           Name = "Label3"
	
	        ADD OBJECT spnspeed AS spinner WITH ;
	           Height = 25, ;
	           Left = 85, ;
	           Top = 192, ;
	           Width = 72, ;
	           Value = 1000, ;
	           Name = "spnSpeed"
	
	        ADD OBJECT command3 AS commandbutton WITH ;
	           Top = 72, ;
	           Left = 132, ;
	           Height = 37, ;
	           Width = 96, ;
	           Caption = "Show Balloon", ;
	           Name = "Command3"
	
	        ADD OBJECT spnleft AS spinner WITH ;
	           Height = 24, ;
	           Left = 97, ;
	           Top = 161, ;
	           Width = 60, ;
	           Value = 50, ;
	           Name = "spnLeft"
	
	        ADD OBJECT label4 AS label WITH ;
	           Caption = "Position Left", ;
	           Height = 25, ;
	           Left = 12, ;
	           Top = 161, ;
	           Width = 72, ;
	           Name = "Label4"
	
	        ADD OBJECT command2 AS commandbutton WITH ;
	           Top = 72, ;
	           Left = 252, ;
	           Height = 37, ;
	           Width = 96, ;
	           Caption = "Hide Genie", ;
	           Name = "Command2"
	
	        ADD OBJECT command4 AS commandbutton WITH ;
	           Top = 144, ;
	           Left = 240, ;
	           Height = 25, ;
	           Width = 37, ;
	           Caption = "Up", ;
	           Name = "Command4"
	
	        ADD OBJECT command5 AS commandbutton WITH ;
	           Top = 192, ;
	           Left = 240, ;
	           Height = 25, ;
	           Width = 37, ;
	           Caption = "Down", ;
	           Name = "Command5"
	
	        ADD OBJECT command6 AS commandbutton WITH ;
	           Top = 168, ;
	           Left = 204, ;
	           Height = 25, ;
	           Width = 37, ;
	           Caption = "Left", ;
	           Name = "Command6"
	
	        ADD OBJECT command7 AS commandbutton WITH ;
	           Top = 168, ;
	           Left = 276, ;
	           Height = 25, ;
	           Width = 37, ;
	           Caption = "Right", ;
	           Name = "Command7"
	
	        PROCEDURE Unload
	           RELEASE oGenie
	           RELEASE oAgent
	        ENDPROC
	
	        PROCEDURE command1.Click
	           oGenie.Speak(ThisForm.Text1.Value)
	        ENDPROC
	
	        PROCEDURE cmdmove.Click
	
	            *-- Move the character to the location indicated in the
	            *-- spinners.
	           oGenie.MoveTo(ThisForm.spnLeft.Value, ;
	                 ThisForm.spnTop.Value, ThisForm.spnSpeed.Value)
	        ENDPROC
	
	        PROCEDURE command3.Click
	
	            *-- Show or hide the text balloon used when speaking.
	           IF this.caption = "Hide Balloon"
	              oGenie.Balloon.Visible = .f.
	              this.caption = "Show Balloon"
	           ELSE
	              oGenie.Balloon.Visible = .t.
	              this.caption = "Hide Balloon"
	           ENDIF
	        ENDPROC
	
	        PROCEDURE command2.Click
	
	               *-- Show or hide the character
	           IF this.Caption = "Hide Genie"
	              oGenie.Hide
	              this.Caption = "Show Genie"
	           ELSE
	              oGenie.Show
	              this.Caption = "Hide Genie"
	           ENDIF
	        ENDPROC
	
	        PROCEDURE command4.Click
	
	               *-- Move the character up, relative to its current
	               *-- position.
	               oGenie.MoveTo(oGenie.Left, oGenie.Top - 50,;
	                 thisform.spnSpeed.Value)
	        ENDPROC
	
	        PROCEDURE command5.Click
	
	               *-- Move the character down, relative to its current
	               *-- position.
	           oGenie.MoveTo(oGenie.Left, oGenie.Top + 50,;
	                 thisform.spnSpeed.Value)
	        ENDPROC
	
	        PROCEDURE command6.Click
	
	               *-- Move the character left, relative to its current
	               *-- position.
	           oGenie.MoveTo(oGenie.Left - 50, oGenie.Top,;
	                 thisform.spnSpeed.Value)
	        ENDPROC
	
	        PROCEDURE command7.Click
	
	               *-- Move the character left, relative to its current
	               *-- position.
	           oGenie.MoveTo(oGenie.Left + 50, oGenie.Top,;
	                 thisform.spnSpeed.Value)
	        ENDPROC
	
	     ENDDEFINE
	     *
	     *-- EndDefine: form1
	     **************************************************
	     *-- Code ends here
	
	REFERENCES
	==========
	
	(c) Microsoft Corporation 1998. All Rights Reserved. Contributions by Mike
	Stewart, Microsoft Corporation
	
	
	Additional query words: kbVFp600 kbAnimantion kbinterop msagent
	
	======================================================================
	Keywords          : kbvfp300 kbvfp500 kbvfp600 kbGrpDSFox kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
