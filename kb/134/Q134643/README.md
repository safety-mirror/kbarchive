---
layout: page
title: "Q134643: FIX: Alter Table Add Primary Key Error Not Trappable"
permalink: /kb/134/Q134643/
---

## Q134643: FIX: Alter Table Add Primary Key Error Not Trappable

{% raw %}

	Article: Q134643
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300bBUG kbvfp500bug kbvfp500fixkbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an existing ON ERROR routine is in effect, the following command causes an
	error, but that error is not trapped by the error routine.
	
	  ALTER TABLE <tablename> ADD PRIMARY KEY <existing key tag>
	
	Instead running the error handler, Visual FoxPro presents a message box titled
	"Microsoft Visual FoxPro" that contains the message "Primary key already
	exists," and it offers the options of OK and Help.
	
	The Help text topic states:
	
	  Primary key already exists. (1883)
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been corrected in Visual FoxPro
	5.0 for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Write a simple program, such as the following program, to illustrate this
	  error and the error as it should be handled.
	
	     ON ERROR WAIT WINDOW "Error"
	     switch=.F.
	     OPEN DATABASE C:\VFP\Samples\Data\testdata.dbc
	     SELECT Customer
	     DO WHILE .T.
	       IF !switch
	         ALTER TABLE Customer ADD PRIMARY KEY cust_id
	       ELSE
	         ALTER TABLE Customer ADD cust_id PRIMARY KEY
	       ENDIF
	       switch=!switch
	     ENDDO
	
	2. Name this program Altertst and save it.
	
	3. In the Command window, enter the DO Altertst command.
	
	4. Press ENTER at each pause
	
	5. After successfully observing the two error modes, press ESC to cancel.
	
	6. In the Visual FoxPro default directory, you will find an error log created in
	  response to the ON ERROR handler named Altertst.err. This is a text file and
	  may be read. It will have the offending line number and the report that the
	  line has a syntax error.
	
	7. Rerun the program. When the Microsoft Visual FoxPro message box appears,
	  click the Help button to see the help text.
	
	Additional query words: 3.00 5.00 handler
	
	======================================================================
	Keywords          : kbvfp kbvfp300bBUG kbvfp500bug kbvfp500fix kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b
	Version           : WINDOWS:3.0,3.0b
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
