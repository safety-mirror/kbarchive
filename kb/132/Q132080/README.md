---
layout: page
title: "Q132080: HOWTO: Change the Color of an MFC Child Control Class"
permalink: /kb/132/Q132080/
---

## Q132080: HOWTO: Change the Color of an MFC Child Control Class

{% raw %}

	Article: Q132080
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,1.51,1.52,2.0,2.1,2.2,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbGDI kbMFC KbUIDesign kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 kbGrpDSMF
	Last Modified: 15-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 2.2, 4.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	- Microsoft Windows XP Home Edition 
	- Microsoft Windows XP Professional 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To change the color scheme of a standard class of controls in an MFC-based
	application, follow these steps:
	
	1. Derive a class from the standard control class, such as CEdit.
	
	2. Define a static member variable of class CBrush to be the brush for that
	  class of controls.
	
	3. Override the control's member function OnChildNotify(), handle the message
	  WM_CTLCOLOR, and use the new brush. In MFC 4.0, this could also be done by
	  using an ON_WM_CTLCOLOR_REFLECT handler.
	
	NOTE: In 32-bit Windows, the controls do not send the WM_CTLCOLOR message. They
	send WM_CTLCOLORxxx messages, where xxx is the type of control. For example,
	static control sends the WM_CTLCOLORSTATIC message.
	
	MORE INFORMATION
	================
	
	This approach works for list boxes, the list boxes of combo boxes, button
	controls, edit controls, static controls, message boxes, and dialog boxes. (This
	approach does not work for push buttons and the CRichEditCtrl. The color of a
	standard CButton object is determined by system settings. If you want a
	different color for push buttons, use a CBitmapButton. To change the color of a
	CRichEditCtrl use its member functions.)
	
	For an alternative approach, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q117778 Changing the Background Color of an MFC Edit Control
	
	It illustrates how to change the background color of a control in the parent
	window.
	
	When a control is about to be redrawn, it sends the message WM_CTLCOLOR to its
	parent. This message is handled by the OnCtlColor() member function of the
	parent.
	
	OnCtlColor() allows the parent to modify the drawing of the child by:
	
	- Specifying the background brush.
	
	- Changing the text color.
	
	- Making other changes to the device context with which the drawing is to be
	  done.
	
	One of the first things the default implementation of OnCtlColor() does is to
	call the OnChildNotify() member function of the child that sent the message. By
	overriding this OnChildNotify() member function, the child can determine its own
	color scheme, instead of taking it from the parent.
	
	The following sample code defines a class of edit controls with red text on a
	green background. The sample code shows only what is necessary to change the
	color of the controls. It does not include code generated by the ClassWizard.
	
	Sample Code
	-----------
	
	     /* Compile options needed:  Default
	     */ 
	
	     // NOTE:  The sample code is for 32-bit. It has to be modified for
	     // 16-bit. See the comment below.
	
	     // ** MYEDIT.H **
	
	     class CMyEdit : public CEdit
	     {
	     public:
	        BOOL OnChildNotify(UINT message, WPARAM wParam, LPARAM Param,
	            LRESULT* pLResult);
	     protected:
	        static CBrush m_brush;
	     };
	
	     // ** MYEDIT.CPP **
	
	     #include "myedit.h"
	
	     // Create a green brush for the background for the class of controls:
	     CBrush CMyEdit::m_brush(RGB(0,128,0));
	
	     BOOL CMyEdit::OnChildNotify(UINT message, WPARAM wParam,
	                                 LPARAM lParam, LRESULT* pLResult)
	     {
	     // If "message" is not the message you're after, do default processing:
	
	     // For 16-bit applications change WM_CTLCOLOREDIT to WM_CTLCOLOR
	        if (message != WM_CTLCOLOREDIT)
	        {
	           return CEdit::OnChildNotify(message,wParam,lParam,pLResult);
	        }
	
	     // Set the text foreground to red:
	        HDC hdcChild = (HDC)wParam;
	        SetTextColor(hdcChild, RGB(0,0,255));
	
	     // Set the text background to green:
	        SetBkColor(hdcChild, RGB(0,128,0));
	
	     // Send what would have been the return value of OnCtlColor() - the
	     // brush handle - back in pLResult:
	        *pLResult = (LRESULT)(m_brush.GetSafeHandle());
	
	     // Return TRUE to indicate that the message was handled:
	        return TRUE;
	     }
	
	Additional query words: 2.50 2.51 2.52 3.00 3.10 3.20
	
	======================================================================
	Keywords          : kbCtrl kbGDI kbMFC KbUIDesign kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbWinXPHome kbWinXPPro kbAudDeveloper kbMFC kbWinXPProSearch kbWinXPHomeSearch kbWinXPSearch kbVCNET
	Version           : :1.0,1.5,1.51,1.52,2.0,2.1,2.2,4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
