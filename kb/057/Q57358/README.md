---
layout: page
title: "Q57358: Incorrect Declaration of Far Procedure in Assembly; BASIC 7.10"
permalink: /kb/057/Q57358/
---

## Q57358: Incorrect Declaration of Far Procedure in Assembly; BASIC 7.10

{% raw %}

	Article: Q57358
	Product(s): See article
	Version(s): 7.00 7.10 | 7.00 7.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | SR# S891226-6 docerr | mspl13_basic
	Last Modified: 8-JAN-1991
	
	On Page 495 of the "Microsoft BASIC 7.0: Programmer's Guide" (for 7.00
	and 7.10), the "proc far" declaring the assembly procedures as far
	should actually be just "far", not "proc far" as shown below.
	
	The following is incorrect:
	
	   extrn stringassign:proc far
	
	It should be the following:
	
	   extrn stringassign:far
	
	This information applies to Microsoft BASIC Professional Development
	System (PDS) versions 7.00 and 7.10 for MS-DOS and MS OS/2.

{% endraw %}
