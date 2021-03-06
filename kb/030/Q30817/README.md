---
layout: page
title: "Q30817: MASM 5.10 OS2.DOC: OS/2 Call Summary - Session Management"
permalink: /kb/030/Q30817/
---

## Q30817: MASM 5.10 OS2.DOC: OS/2 Call Summary - Session Management

{% raw %}

	Article: Q30817
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_masm
	Last Modified: 26-MAY-1988
	
	The following information is from the Microsoft Macro Assembler
	Version 5.10 OS2.DOC file.
	
	OS/2 Call Summary
	Session management constant - INCL_DOSSESMGR
	
	   @DosStartSession - Starts a new session
	   Parameters - StartData:PS, SessID:PW, PID:PW
	   Structure - STARTDATA
	
	   @DosSetSession - Sets status of a child process
	   Parameters - SessID:W, StatusData:PS
	   Structure - STATUSDATA
	
	   @DosSelectSession - Enables a parent process to switch a child to
	                       foreground
	   Parameters - SessID,W, Reserved:D
	
	   @DosStopSession - Terminates session previously started with
	                     DosStartSession
	   Parameters - TargetOption:W, SessID:W, Reserved:D

{% endraw %}
