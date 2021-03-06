---
layout: page
title: "Q315535: BUG: Problems When You Rebuild Static and Dynamic CRT Libraries"
permalink: /kb/315/Q315535/
---

## Q315535: BUG: Problems When You Rebuild Static and Dynamic CRT Libraries

{% raw %}

	Article: Q315535
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbCompiler kbCRT
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Editions, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to rebuild the Visual C++ 6.0 C Runtime (CRT) Libraries (Static or
	Dynamic), you may experience some problems.
	
	NOTE: Microsoft does not recommend rebuilding the CRT libraries. Microsoft may
	not be able to provide support for problems encountered when using rebuilt CRT
	libraries. You are not permitted to redistribute a rebuilt DLL with the same
	name used by Microsoft.
	
	CAUSE
	=====
	
	Makefile contains extra lines that cause errors during rebuild. Also, Makefile
	contains entries that are not valid.
	
	RESOLUTION
	==========
	
	To work around these errors, you must perform the following procedures:
	
	Prerequisites
	-------------
	
	1. The default installation of Visual C++ 6.0 does not install the CRT Source
	  code directory. If you copy this directory manually from the installation
	  CD-ROM, the directory tree will not be set properly. To install the CRT
	  Source directory, follow these steps:
	
	  a. On the Start menu, click Control Panel, and then click Add or Remove
	     Programs.
	
	  b. On the Currently Installed Programs list, click Microsoft Visual C++ 6.0.
	
	  c. Click Change/Remove.
	
	  d. In the Visual C++ 6.0 Setup dialog box, click Add/Remove.
	
	  e. Click to select CRT Source Code.
	
	  f. Click OK.
	
	2. Manually copy the following files from the Visual C++ installation CD-ROM to
	  C:\Program Files\Microsoft Visual Studio\Vc98\Crt\Src:
	
	   - Makefile
	   - Makefile.inc
	   - Makefile.sub
	
	  NOTE: By default, Visual C++ is installed in the C:\Program Files\Microsoft
	  Visual Studio folder. If you have installed Visual C++ in another location,
	  make sure that you modify the path in all of the examples in this article.
	
	3. Change the file attributes of Makefile in C:\Program Files\Microsoft Visual
	  Studio\Vc98\Crt\Src. To do this, follow these steps:
	
	  a. In Windows Explorer, right-click Makefile, and then click Properties.
	
	  b. Click to clear the check box for the Read-only file attribute.
	
	  c. Click OK.
	
	4. In a text editor such as Notepad, make the following changes to Makefile:
	
	  a. Change the three lines that start at line 38 so that they resemble the
	     following sample code:
	
	  #!if "$(V6TOOLS)"==""
	  V6TOOLS=C:\Program Files\Microsoft Visual Studio\vc98
	  #!endif  
	
	     NOTE: Do not place double-quotes around the path designation.
	
	  b. By default, line 331 appears as follows:
	
	  RC_INCS=-I$(V6TOOLS)\include
	
	If the name of your Visual C++ 6.0 installation directory contains spaces, then
	you must change line 331 by adding double quotes as follows:
	
	RC_INCS=-I"$(V6TOOLS)\include"
	
	  c. Search for every instance of Winver.h in Makefile, and then use the #
	     symbol to comment out each line that includes Winver.h, as shown in the
	     following sample code:
	
	  # $(V6TOOLS)\include\winver.h \ 
	
	5. Save your changes to Makefile, and then close the text editor.
	
	Steps to Rebuild the Libraries
	------------------------------
	
	The environment must be configured properly before you can rebuild Makefile. To
	configure the environment, and then rebuild Makefile, follow these steps:
	
	1. If the Visual C++ environment variables are not set, then run the following
	  batch file:
	
	  C:\Program Files\Microsoft Visual Studio\Vc98\Bin\Vcvars32.bat
	
	  NOTE: You may have to increase the environment space if your operating system
	  is Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows
	  Millennium Edition (Windows Me). For additional information, click the
	  article number below to view the article in the Microsoft Knowledge Base:
	
	  Q248802 PRB: Vcvars32.bat Generates Out of Environment Message
	
	  NOTE: If your computer has multiple versions of the C++ compiler (Cl.exe), run
	  Vcvars32.bat to avoid unexpected results that may occur if you use the Visual
	  C++ .NET compiler instead of the Visual C++ 6.0 compiler.
	
	2. At a command prompt, go to the C:\Program Files\Microsoft Visual
	  Studio\Vc98\Crt\Src directory, and then run the command NMAKE. NMAKE builds
	  all of the static and dynamic libraries. The libraries are placed in the
	  C:\Program Files\Microsoft Visual Studio\Vc98\Crt\Src\Build\Intel directory.
	
	  NOTE: You can run the command Bldnt.cmd instead of NMAKE. However, if you are
	  building Makefile on a computer running Windows 95, Windows 98, or Windows
	  Me, then you must run the batch file Bldwin95.bat instead of Bldnt.cmd.
	
	By default, Makefile builds Msvcrt.dll as _sample_.dll, Msvcrtd.dll as
	_sampld_.dll, Msvcrti.dll as _sample_i.dll, and so on.
	
	Makefile contains the following entries for the default names. If you want to
	change the default library names, change them in Makefile first. Be careful
	about your choice of names because some names have leading underscores and you
	must find the corresponding names in other files.
	
	- RETAIL_DLL_NAME=_sample_
	- RETAIL_LIB_NAME=_sample_
	- RETAIL_DLLCPP_NAME=sample_p
	- RETAIL_LIBCPP_NAME=sample_p
	- RETAIL_DLLIOS_NAME=sample_i
	- RETAIL_LIBIOS_NAME=sample_i
	- DEBUG_DLL_NAME=_sampld_
	- DEBUG_LIB_NAME=_sampld_
	- DEBUG_DLLCPP_NAME=sampld_p
	- DEBUG_LIBCPP_NAME=sampld_p
	- DEBUG_DLLIOS_NAME=sampld_i
	- DEBUG_LIBIOS_NAME=sampld_i
	
	The following are the corresponding .rc and .def files with the default names:
	
	- Sampld_i.def
	- Sampld_p.def
	- Sample_i.def
	- Sample_i.rc
	- Sample_p.def
	- Sample_p.rc
	- _sample_.rc
	- _sample_.def
	- _sampld_.def
	
	These files are located in the following directories:
	
	- C:\Program Files\Microsoft Visual Studio\Vc98\Crt\Src
	
	- C:\Program Files\Microsoft Visual Studio\Vc98\Crt\Src\Intel
	
	You can rename these files to the names that you want. To do this, open the
	individual files, one at a time, and then change the corresponding names in the
	files to reflect the new names that you give to the files themselves. For
	example, if you want to change the default library name, Open _sample_.def. The
	file has the following line:
	
	  LIBRARY _SAMPLE_
	
	Modify that line to the library name that you want to use, such as the
	following:
	
	LIBRARY <I BRACKET="YES">mycrtlibname</I>
	
	When you finish building the library, your application links to the resulting
	import library, <mycrtlibname>.lib.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q234622 PRB: VC++ 6.0 Setup Does Not Copy the CRT Make Files
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCompiler kbCRT 
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch
	Version           : :6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
