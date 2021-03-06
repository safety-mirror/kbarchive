---
layout: page
title: "Q295565: Microsoft Project 2000 Step By Step Comments And Corrections"
permalink: /kb/295/Q295565/
---

## Q295565: Microsoft Project 2000 Step By Step Comments And Corrections

{% raw %}

	Article: Q295565
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft Project 2000 Step by Step ISBN 0-7356-0920-9 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information about known errors
	relating to the Microsoft Press book Microsoft Project 2000 Step By Step, ISBN
	0-7356-0920-9 .
	
	The following topics are covered:
	
	- CD-ROM: Project 2000 Evaluation Version Expired
	
	- Pages xiv and xvii: Incorrect Instructions
	
	- Page 28: Incorrect Step
	
	- Page 32: Incorrect MOUS Objective
	
	- Page 34: Should Include MOUS Objective Icon In Margin
	
	- Page 46: Incorrect MOUS Objective Listed
	
	- Page 110: Lead Time And Lag Time Descriptions Reversed
	
	- Page 138: Incomplete MOUS Objective
	
	- Page 165: MOUS Icon Should List Only One Objective
	
	- Page 165: Incorrect Description
	
	- Page 186: Incorrect Reference to "Resource"
	
	- Page 281: Missing Step
	
	- Page 293: Tasks Are Not Effected
	
	- Page 323: "Pre-Production" Should Be "Production"
	
	- Page 423: Page 423: Incorrect Page Listed For "Effort-Driven Scheduling"
	
	MORE INFORMATION
	================
	
	CD-ROM: Project 2000 Evaluation Version Expired
	-----------------------------------------------
	
	After installing the Project 2000 Evaluation software, you may receive an error
	that the software is expired.
	
	To work around this problem, manually reset the FirstBoot registry entry to 1. To
	do this, follow these steps:
	
	NOTE: This workaround allows the Evaluation version to run successfully during
	the allotted time frame. Setting the FirstBoot setting back to 1 after the
	evaluation period has expired does not allow the Evaluation to work for an
	extended period of time.
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "regedit" (without the quotation marks).
	
	3. In the left pane of Registry Editor, navigate to and select the following
	  subkey (folder):
	  HKEY_CURRENT_USER/Software/Microsoft/Office/9.0/MSProject/Options/General
	
	4. In the right pane, double-click the FirstBoot entry.
	
	5. In the "Value data" box, delete the "0" and type "1" (without the quotation
	  marks), then click OK.
	
	6. On the Registry menu, click Exit.
	
	You can now run the Evaluation version properly during the allotted time frame.
	
	
	Pages xiv and xvii: Incorrect Instructions
	------------------------------------------
	
	On pages xiv and xvii, the steps under "Installing the Practice Files" and "Using
	the Multimedia Files" are incorrect. Please refer to the readme.txt file on the
	CD-ROM for the correct steps.
	
	
	Page 28: Incorrect Step
	-----------------------
	
	On page 28, under "Lesson Wrap-Up", in step 1, remove the last sentence.
	
	Remove:
	"Save the file with a baseline."
	
	
	Page 32: Incorrect MOUS Objective
	---------------------------------
	
	On page 32, remove the MOUS objective icon.
	
	
	Page 34: Should Include MOUS Objective Icon In Margin
	-----------------------------------------------------
	
	On page 34, the icon for the MOUS objective PROJ2000-1-5 should be noted in the
	margin next to the topic "Estimating Durations".
	
	
	Page 46: Incorrect MOUS Objective Listed
	----------------------------------------
	
	On page 46 the MOUS icon includes the incorrect MOUS objective. Change:
	
	"PROJ2000-4-3"
	
	To:
	"PROJ2000-1-14"
	
	
	Page 110: Lead Time And Lag Time Descriptions Reversed
	------------------------------------------------------
	
	The second sentence in the second to last paragraph on page 110 has lead time and
	lag time reversed. Change:
	
	"Lead time is entered in positive units, lag time in negative units (for example,
	-2 days or -50%)."
	
	To:
	"Lag time is entered in positive units, lead time in negative units (for example,
	-2 days or ?50%)."
	
	
	Page 138: Incomplete MOUS Objective
	-----------------------------------
	
	On page 138, there should be two objective numbers listed under the MOUS icon.
	
	Change:
	"PROJ2000-3-2"
	
	To:
	"PROJ2000-3-2
	PROJ2000-1-20"
	
	
	Page 165: MOUS Icon Should List Only One Objective
	--------------------------------------------------
	
	Two MOUS objectives are listed on page 165, for PROJ2000-1-3 and PROJ2000E-1-5.
	Objective PROJ2000-1-3 should be removed.
	
	
	Page 165: Incorrect Description
	-------------------------------
	
	On page 165, the last sentence should refer to the Resource Graph view.
	
	Change:
	"In this split view, the Resource Usage view appears below the Gantt Chart
	view."
	
	To:
	"In this split view, the Resource Graph view appears below the Gantt Chart
	view."
	
	
	Page 186: Incorrect Reference to "Resource"
	-------------------------------------------
	
	In the paragraph under step 7 on page 186, change:
	
	"Microsoft Project scrolls vertically to Resource 2,"
	
	To:
	"Microsoft Project scrolls vertically to Task 2,"
	
	
	Page 281: Missing Step
	----------------------
	
	On page 281, in step 1, add the following step above the sentence "The Resource
	Information dialog box appears".
	
	"On the Standard toolbar, click the Resource Information button."
	
	
	Page 293: Tasks Are Not Effected
	--------------------------------
	
	On page 293, in the 2nd bulleted item, change the last sentence from:
	"Tasks from inserted projects are affected."
	
	To:
	"Tasks from inserted projects are not effected."
	
	
	Page 323: "Pre-Production" Should Be "Production"
	-------------------------------------------------
	
	In the first bulleted item on page 323, change:
	
	"... task and then to the 'Pre-Production' summary task."
	
	To:
	"... task and then to the "Production" summary task."
	
	
	Page 423: Incorrect Page Listed For "Effort-Driven Scheduling"
	--------------------------------------------------------------
	
	On page 423 in the Index, under "Task types", the entry for effort-driven
	scheduling should refer you to page 114.
	
	Change:
	"effort-driven scheduling and, 14"
	
	To:
	"effort-driven scheduling and, 114"
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: OFF2000 0-7356-0920-9 Chatfield Johnson
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
