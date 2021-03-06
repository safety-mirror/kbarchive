---
layout: page
title: "Q37778: Emulator Math Operations in My DLL that Uses LLIBCDLL"
permalink: /kb/037/Q37778/
---

## Q37778: Emulator Math Operations in My DLL that Uses LLIBCDLL

{% raw %}

	Article: Q37778
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 14-NOV-1988
	
	Question:
	
	I am using LLIBCDLL.LIB for my DLL. This library is supposed to use
	the alternate math package; however, when I compile and link, it
	appears to get emulator instructions in the code and my DLL does not
	act correctly. Where are these emulator instructions coming from, and
	how do I get rid of them?
	
	Response:
	
	Most likely the problem is that you are not using the /FPa switch on
	the compile line. You need this switch or the compiler assumes the
	emulator math package (default) and puts emulator math commands in
	your code. When this emulator math code is linked with LLIBCDLL.LIB,
	which uses alternate math, it will not work correctly.

{% endraw %}
