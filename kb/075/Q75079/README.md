---
layout: page
title: "Q75079: FIX: NMAKE 1.13 May Return U1002: Invalid Macro Invocation '&#36;'"
permalink: /kb/075/Q75079/
---

## Q75079: FIX: NMAKE 1.13 May Return U1002: Invalid Macro Invocation '&#36;'

{% raw %}

	Article: Q75079
	Product(s): Microsoft Programming Utilities
	Version(s): 1.13
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 21-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft NMAKE Utility for MS-DOS, version 1.13, on platform(s):
	   - the operating system: MS-DOS 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	NMAKE version 1.13 generates the following error when an "extra" dollar sign ($)
	is used in an environment variable:
	
	  fatal error U1002: syntax error : invalid macro invocation '$'
	
	CAUSE
	=====
	
	Unlike previous versions, NMAKE version 1.13 evaluates all environment variables
	as inherited macros at initialization time. Because the $ character indicates
	that a macro follows, NMAKE attempts to evaluate the character following the
	final dollar sign in the context of a macro. For example, using a command such
	as "Prompt $p$g$" to set the system prompt, and then using NMAKE 1.13, causes
	this error.
	
	RESOLUTION
	==========
	
	The online help for the U1002 error indicates that it occurs when a single
	dollar sign ($) appears without a macro name associated with it. This error can
	be eliminated by avoiding extraneous dollar signs in environment variables.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in NMAKE version 1.13 for MS-DOS
	and OS/2. This problem was corrected in NMAKE version 1.2 for MS-DOS and OS/2.
	
	Additional query words: 1.13 buglist1.13 fixlist1.20
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbVCsearch kbAudDeveloper kbNMAKESearch
	Version           : :1.13
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
