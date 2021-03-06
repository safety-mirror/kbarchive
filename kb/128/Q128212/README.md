---
layout: page
title: "Q128212: PRB: Error LNK2001 Generated When Porting 16-bit Code to Win32"
permalink: /kb/128/Q128212/
---

## Q128212: PRB: Error LNK2001 Generated When Porting 16-bit Code to Win32

{% raw %}

	Article: Q128212
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbtshoot kbVC200 kbVC210 kbVC400 kbVC500 kbVC600
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 2.0, 2.1, 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Porting your 16-bit application to Win32 results in LINK error LNK2001
	(unresolved externals), if a __cdecl function is exported using a module-
	definition (.DEF) file. The error specifies the function as defined in the .DEF
	file, with the leading underscore (_) in the name.
	
	CAUSE
	=====
	
	In 16-bit code, functions are either declared with the __cdecl, __pascal, or
	__fastcall conventions. The linker should not resolve a call to a __cdecl
	function with a __pascal function, therefore, the compiler decorates __cdecl
	names with a leading underscore, converts __pascal names to all caps, and
	decorates __fastcall functions with a leading at symbol (@), so the linker will
	not make this mistake. It is a requirement that you put the decorated name in
	the .DEF file.
	
	In 32-bit code for the x86, functions are either declared with the __cdecl,
	__stdcall, or __fastcall conventions. The compiler decorates __cdecl names with
	a leading underscore, __stdcall names with a leading underscore and an appended
	@N (where N is the number of bytes in the parameter list), and __fastcall names
	with a leading at symbol (@) and an appended @N (where N is the number of bytes
	in the parameter list).
	
	The 32-bit linker uses a different method to resolve function calls, so a single
	.DEF file can be compatible across all Win32 platforms, including RISC, where
	the names are not decorated in a similar manner. You specify the undecorated
	name in the .DEF file and pass the object file(s) to the linker when building
	the import library. The linker will do a fuzzy lookup, comparing the undecorated
	names to the decorated names in the object file to find a match.
	
	In the case mentioned in the Symptoms section of this article, the function name
	already has the leading underscore, whereas the linker is expecting an
	undecorated name. Suppose the function is MyFunc and the .DEF file contains
	_MyFunc. The decorated name is _MyFunc, but the linker searches for __MyFunc,
	__MyFunc@N, and @_MyFunc@N and cannot resolve the reference.
	
	RESOLUTION
	==========
	
	To work around the problem, update your .DEF file by removing the underscore at
	the beginning of the file name. If you are maintaining the same source code with
	both Visual C++ for Windows and Visual C++ 32-bit Edition, you must use two .MAK
	(project) files and two .DEF files, one for each environment. However, the one
	32-bit .DEF file will work across all Win32 platforms.
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbtshoot kbVC200 kbVC210 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC500 kbVC600 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : winnt:2.0,2.1,4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
