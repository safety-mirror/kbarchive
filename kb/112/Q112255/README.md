---
layout: page
title: "Q112255: PC Ext: Session Log File Maintenance"
permalink: /kb/112/Q112255/
---

## Q112255: PC Ext: Session Log File Maintenance

{% raw %}

	Article: Q112255
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:2.1,3.0,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 2.1, 3.0, 3.2, on platform(s):
	   - the operating system: MS-DOS 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When the External Mail program runs on a highly used Microsoft Mail network, the
	SESSION.LOG file can become very large. Because this file is continually updated
	(by the External Mail program), it is locked open at all times. This may
	restrict a Mail administrator from archiving logged information conveniently.
	The following information is provided to help in these situations.
	
	There are two issues related to the management of the SESSION.LOG file:
	
	- The SESSION.LOG file is locked by the External Mail program
	
	- There is limited disk space
	
	SESSION.LOG File is Locked by External
	--------------------------------------
	
	This issue can be resolved by using an appropriate text editor. For example,
	Microsoft Word for Windows can open locked files by making a copy. In this
	manner, you can open and check the SESSION.LOG file while the External Mail
	program is still running.
	
	Limited Disk Space
	------------------
	
	This issue is more prevalent in organizations where either disk space is limited,
	or log file archiving is required. If you need to control the size of the
	SESSION.LOG file on a scheduled basis, you will need to create a utility that
	can rename the SESSION.LOG file at scheduled times. To do this, you need to use
	the Break Time option (as explained on page 242 of the Microsoft Mail 3.2
	"Administrator's Guide"). The Break Time option enables you to halt the External
	Mail program, access SESSION.LOG to perform archiving, and then resume the
	External Mail program automatically.
	
	The following code is an example of a REXX file that is called from a command
	file named EXTRN1.CMD. This file uses the current date as a code name for all
	archived files. It also uses an OS/2 version of PKZIP.EXE (ZIP.EXE). If you
	choose to use this shareware product please register per its documentation.
	
	      /* Log File Management */ 
	
	     /* Prepare a code name for archived Log Files */ 
	     Today1=date('s')
	     Say (' Today is ''')
	     /* Parse the parameter down to six characters */ 
	     Today2=DELSTR(Today1,1,2)
	
	     /* If today's archive exists, exit back to external.   */ 
	     /* If it does not, zip logs into an archive directory. */ 
	
	     'If exist c:\mmta\log\archive\AR'Today2'.zip call
	        f:\External\Extrn1.cmd'
	     'zip c:\mmta\log\AR'Today2'.zip *.*'
	     'copy c:\mmta\log\AR'today2'.zip archive\*.*'
	
	     /* If archiving is unsuccessful, do not delete the active */ 
	     /* log files. All further logging will be appended to the */ 
	     /* active logs. */ 
	
	     'If exist C:\mmta\log\archive\AR'Today2'.zip erase
	        c:\molotov\mmta\log\*.log'
	
	     /* Loop back to the External Command file */ 
	     'call f:\External\Extrn1.cmd'
	
	Additional query words: 2.10 3.00 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3
	Version           : WINDOWS:2.1,3.0,3.2
	
	=============================================================================
	

{% endraw %}
