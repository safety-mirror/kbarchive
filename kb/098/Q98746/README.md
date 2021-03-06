---
layout: page
title: "Q98746: PRB: SET DEVICE TO PRINTER PROMPT Does Not Open Dialog Box"
permalink: /kb/098/Q98746/
---

## Q98746: PRB: SET DEVICE TO PRINTER PROMPT Does Not Open Dialog Box

{% raw %}

	Article: Q98746
	Product(s): Microsoft FoxPro
	Version(s): 2.5x,2.6x,3.0,6.0,7.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 6.0, 7.0 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6x 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Issuing the SET PRINTER ON PROMPT or SET DEVICE TO PRINTER PROMPT command
	immediately after issuing the same command does not produce the expected
	Microsoft Windows Print dialog box.
	
	CAUSE
	=====
	
	Once the printer has been defined, FoxPro does not display the Print dialog box
	again until the printer is once again in an undefined state. For example, this
	problem will occur if the previous print job has not yet been released by Print
	Manager or the network spooler.
	
	RESOLUTION
	==========
	
	To work around this problem, do one of the following:
	
	- Add the command SET PRINTER TO to the end of your program so the print job
	  will be released each time the program is run and consequently, the Print
	  dialog box will appear every time.
	
	  -or-
	
	- Use the following code sequence after the print job is completed:
	
	     SET PRINTER OFF        && disables output to the printer.
	     SET PRINTER TO         && resets output to default MS-DOS PRN print
	                            && utility
	
	  NOTE: The SET PRINTER TO command causes a page to be ejected from the printer.
	  A workaround to this behavior is not known at this time.
	
	STATUS
	======
	
	This behavior is by design.
	
	
	MORE INFORMATION
	================
	
	To reproduce the problem, run the following program twice:
	
	     SET DEVICE TO PRINTER PROMPT
	     @ 3,3 SAY 'HELLO,WORLD'
	     SET DEVICE TO SCREEN
	
	The first time the program is run, the Print dialog box will appear as expected.
	The second time the program is run, the dialog box will not appear although both
	print jobs are in the print queue.
	
	NOTE: Both jobs will print if you quit FoxPro for Windows or if you issue the SET
	PRINTER TO command in the Command window. Also, if the Cancel button on the
	prompt is selected, FoxPro ignores this action and sends the @...SAY commands to
	the printer anyway.
	
	REFERENCES
	==========
	
	"Language Reference," version 2.5, page L3-973
	
	Additional query words: VFoxWin FoxWin 2.50 2.50a 2.50b 2.60 2.60a no output device to print prompt kbvfp300 kbvfp600
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbVFP300 kbVFP600 kbVFP700
	Version           : :2.5x,2.6x,3.0,6.0,7.0
	
	=============================================================================
	

{% endraw %}
