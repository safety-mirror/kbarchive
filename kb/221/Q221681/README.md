---
layout: page
title: "Q221681: FIX: Locals Window Not Refreshed with SUSPEND or SET STEP ON"
permalink: /kb/221/Q221681/
---

## Q221681: FIX: Locals Window Not Refreshed with SUSPEND or SET STEP ON

{% raw %}

	Article: Q221681
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix kbGrpDSFox kbDSupport
	Last Modified: 11-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Locals window of the Debugger does not refresh properly when a program
	contains either the SUSPEND or the SET STEP ON commands.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3.
	
	For more information about Visual Studio service packs, please see the following
	articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Open Visual FoxPro and the Debugger. Arrange the windows so that Visual
	  FoxPro is on the right half of the screen, and the Debugger is on the left
	  half. The screens should not overlap.
	
	2. Create a program called Test containing the following code:
	
	  CLEAR ALL
	  DEBUG
	  PUBLIC x
	
	  x = PROGRAM()
	  DO proc1 WITH x
	
	  PROCEDURE proc1
	  LPARAMETERS tx
	  LOCAL x
	  x = tx+' '+PROGRAM()
	  SET STEP ON
	  DO proc2 WITH x
	  ENDPROC
	
	  PROCEDURE proc2
	
	  LPARAMETERS tx
	  LOCAL x
	  x = tx +' '+ PROGRAM()
	  SET STEP ON
	  ?x
	
	3. Leave the Test program open and run the code.
	
	4. Press the Resume [>] toolbar button in the Debugger twice.
	
	5. Press the ALT+TAB keys to go back to Visual FoxPro and run the program again
	  by pressing the CTRL+E keys.
	
	Call Stack window correctly says:
	
	Proc1
	Test.prg
	
	The Locals dropdown correctly says: Proc1. Value of x in Locals window is TEST;
	this is correct value for x in Test, not Proc1, and tx does not appear. If you
	move the Visual FoxPro window over the Debugger Locals window to make it
	repaint, you will see the correct value for x ("TEST PROC1"), but the letters tx
	still do not appear.
	
	6. Press the Resume [>] button in Debugger toolbar.
	
	Observed: Call Stack window correctly says:
	
	Proc2
	Proc1
	Test.prg
	
	The Locals dropdown correctly says Proc2. Value of x in Locals window is TEST or
	TEST PROC1 depending on if you forced a repaint above in observed after step 3.
	This is correct value for x in Test or Proc1, and the letters tx still do not
	appear.
	
	At any time, if you click a program in the Call Stack window, or click on the
	locals dropdown to select a procedure, the Locals Window displays the correct
	values.
	
	To see the behavior with the SUSPEND command, follow these steps:
	
	1. Create and run the following code from a program (.PRG) file:
	
	  DEBUG
	  x = 1
	  SUSPEND
	  x = 3
	
	2. Look at the Locals window.
	
	Notice that x is not visible. If you click on the program name in the Call Stack
	window, x will appear in the Locals window.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix kbGrpDSFox kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
