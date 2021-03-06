---
layout: page
title: "Q187684: BUG: Assert When Calling AfxFreeLibrary from ExitInstance"
permalink: /kb/187/Q187684/
---

## Q187684: BUG: Assert When Calling AfxFreeLibrary from ExitInstance

{% raw %}

	Article: Q187684
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0
	Operating System(s): 
	Keyword(s): kbDLL kbMFC kbVC200bug kbVC400bug kbVC500bug kbOSWin95 kbDSupport kbGrpDSMFCATL
	Last Modified: 19-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 2.0, 2.1, 2.2, 4.0, 4.1, 4.2, 5.0, on platform(s):
	   - the operating system: Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following assertion in Afxcrit.cpp line 73 can fail when you call the
	AfxFreeLibrary function from the ExitInstance function of an MFC DLL:
	
	     ASSERT(!_afxResourceLocked[i]);
	
	Similarly, an access violation or an unhandled exception may occur when you call
	FreeLibrary from ExitInstance or the DllMain function during DLL_PROCESS_DETACH.
	
	CAUSE
	=====
	
	The Windows 95 loader is not reentrant. Causing a DLL to be freed while in the
	process of freeing another DLL can cause a dependent DLL to be freed
	unexpectedly.
	
	For example, if a DLL (A) with a dependant DLL (B) and a reference count of 0
	calls FreeLibrary from DLL_PROCESS_DETACH on another DLL (C), the Windows 95
	unloader rescans the dependent DLL list and prematurely releases the dependent
	DLL (B). The DLL (A) that calls FreeLibrary is protected because it is marked.
	Upon returning from FreeLibrary, DLL (A) might make further calls into DLL (B)
	and cause the assertion or access violation.
	
	RESOLUTION
	==========
	
	Don't call AfxFreeLibrary from ExitInstance. Likewise, don't call FreeLibrary
	from either ExitInstance or from DLL_PROCESS_DETACH of the DllMain function.
	
	You can work around this bug by providing initialization and uninitialization
	functions that are not called from within DllMain. For example, if you use an
	ActiveX DLL, you can call AfxLoadLibrary and AfxFreeLibrary from the COM
	object's constructor and OnFinalRelease function. Calling AfxFreeLibrary from a
	destructor of a static object does not work because the static object
	constructors and destructors are called from DllMain.
	
	An alternative workaround is to increment the reference count of the DLL with a 0
	reference by calling (Afx)LoadLibrary again.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in Windows 95. We are researching this
	bug and will post new information here in the Microsoft Knowledge Base as it
	becomes available.
	
	MORE INFORMATION
	================
	
	In MFC, DLLs are dynamically loaded and unloaded using AfxLoadLibrary and
	AfxFreeLibrary, respectively. A common mistake when using AfxFreeLibrary (or
	FreeLibrary) is to call it from ExitInstance of an MFC DLL. A similar problem
	occurs when you call FreeLibrary from DllMain with DLL_PROCESS_DETACH.
	
	When you call FreeLibrary from DllMain during DLL_PROCESS_DETACH under Windows
	95, the entire dependency tree is reevaluated. If any DLL other than the one
	currently calling FreeLibrary has a reference count of 0, it will be unloaded.
	In some cases, this can cause problems if there are still calls to the unloaded
	DLL.
	
	A common example is when the CRT libraries are prematurely unloaded. To work
	around this problem, you can make an additional call to LoadLibrary for the CRT
	libraries before you call FreeLibrary.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDLL kbMFC kbVC200bug kbVC400bug kbVC500bug kbOSWin95 kbDSupport kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper
	Version           : winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
