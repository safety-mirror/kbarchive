---
layout: page
title: "Q135873: HOWTO: Add Tooltips for Controls on an MFC Modal Dialog Box"
permalink: /kb/135/Q135873/
---

## Q135873: HOWTO: Add Tooltips for Controls on an MFC Modal Dialog Box

{% raw %}

	Article: Q135873
	Product(s): Microsoft C Compiler
	Version(s): 2.1,2.2,4.0,4.1,4.2,4.2b,5.0,6.0
	Operating System(s): 
	Keyword(s): kbCmnCtrls kbCtrl kbDlg kbMFC kbToolTip KbUIDesign kbVC210 kbVC220 kbVC400 kbVC500 kbVC
	Last Modified: 15-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 2.1, 2.2, 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 4.2b, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 4.2b, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To make the CToolTipCtrl class work correctly, you must call the
	CToolTipCtrl::RelayEvent() function. This makes it possible for the mouse
	messages to be passed to the tooltip control.
	
	For a non-modal dialog box window in an MFC application, use the window's
	CWnd::PreTranslateMessage() function to call CToolTipsCtrl::RelayEvent().
	However, for a modal dialog box, the CDialog::PreTranslateMessage() function is
	not called because modal dialog boxes have their own message loops. Therefore,
	to use CToolTipCtrl in a modal dialog box, you need a different approach. This
	article gives a step-by-step example that shows how to use the CToolTipCtrl
	class in a MFC modal dialog box, it involves adding two additional member
	variables to the application class and overwriting the
	CWinApp::ProcessMessageFilter() function for the application class.
	
	MORE INFORMATION
	================
	
	Step-by-Step Example
	--------------------
	
	The following procedure generates a default MFC skeleton application and adds
	tooltips to the OK button on the About dialog box and the dialog box itself:
	
	1. Use the Appwizard in Visual C++ to generate an MFC application, call it
	  Tooltips, and use all the Appwizard default settings.
	
	2. Include the <afxcmn.h> header file in the stdafx.h file.
	
	  NOTE: Do not do this step for Visual C++ .NET.
	
	3. Add the following member variables to the CTooktipsApp class in the
	  Tooltips.h file:
	
	     class CTooltipsApp : public CWinApp
	     {
	        //...
	     public:
	        HWND    m_hwndDialog;
	        CToolTipCtrl*   m_gpToolTip;
	
	        //...
	     };
	
	4. Initiate the two variables in the application's constructor to NULL:
	
	     CTooltipsApp::CTooltipsApp()
	     {
	        m_hwndDialog = NULL;
	        m_gpToolTip = NULL;
	     }
	
	5. Overwrite the CTooltipsApp:: ProcessMessageFilter() function as follows:
	
	     BOOL CTooltipsApp::ProcessMessageFilter(int code, LPMSG lpMsg)
	     {
	        if (m_hwndDialog != NULL)
	            if (lpMsg->hwnd == m_hwndDialog ||
	                ::IsChild(m_hwndDialog, lpMsg->hwnd))
	              {
	                             if (NULL != m_gpToolTip)
	                                     m_gpToolTip->RelayEvent(lpMsg);
	              }
	             return CWinApp::ProcessMessageFilter(code, lpMsg);
	     }
	
	6. Use Classwizard to add a member variable for the OK button in the CAboutDlg
	  class, and call it m_btOK. Also, add a m_pTooltip pointer to a CToolTipCtrl
	  object:
	
	  NOTE: For Visual C++ .NET you can add a memeber variable using the "Class
	  View" right. (Click the AboutDialog calls, and then on Add menu, select Add
	  Variable.)
	
	     class CAboutDlg : public CDialog
	     {
	     public:
	        CAboutDlg();
	
	     // Dialog Data
	        //{{AFX_DATA(CAboutDlg)
	        enum { IDD = IDD_ABOUTBOX };
	        CButton   m_btOK;
	        //}}AFX_DATA
	
	        CToolTipCtrl* m_pTooltip;
	
	        //...
	     };
	
	7. Add code to the CAboutDlg class' constructor and destructor to initialize and
	  release the tooltip object, you might also need to add a default destructor
	  first:
	
	     CAboutDlg::CAboutDlg() : CDialog(CAboutDlg::IDD)
	     {
	        m_pTooltip = NULL;
	     }
	
	     CAboutDlg::~CAboutDlg()
	     {
	        delete m_pTooltip;
	     }
	
	8. Overwrite the OnMouseMove() function of the CAboutDlg class to set up the
	  tooltip control:
	
	     void CAboutDlg::OnMouseMove(UINT nFlags, CPoint point)
	     {
	         //Set up the tooltip
	         if (!m_pTooltip)
	         {
	            int rt;
	             m_pTooltip = new CToolTipCtrl;
	           rt = m_pTooltip->Create(this);
	           ASSERT(rt!=0);
	
	           ((CTooltipsApp*)AfxGetApp())->m_gpToolTip= m_pTooltip;
	
	           rt = m_pTooltip->AddTool(this, "About Box");
	           ASSERT(rt!=0);
	           rt = m_pTooltip->AddTool(&m_btOK,"OK Button");
	           ASSERT(rt!=0);
	
	            m_pTooltip->Activate(TRUE);
	         }
	
	        CDialog::OnMouseMove(nFlags, point);
	     }
	
	9. Overwrite the OnInitDialog() function of the CAboutDlg class to pass the
	  dialog's handle to the application:
	
	     BOOL CAboutDlg::OnInitDialog()
	     {
	        CDialog::OnInitDialog();
	
	        ((CTooltipsApp*)AfxGetApp())->m_hwndDialog=m_hWnd;
	
	        return TRUE;  // return TRUE unless you set the focus to a control
	                      // EXCEPTION: OCX Property Pages should return FALSE
	     }
	
	10. Overwrite the PostNcDestroy() function of the CAboutDlg class to reset the
	  variables in the application class:
	
	     void CAboutDlg::PostNcDestroy( )
	     {
	        CDialog::PostNcDestroy();
	
	        ((CTooltipsApp*)AfxGetApp())->m_hwndDialog= NULL;
	        ((CTooltipsApp*)AfxGetApp())->m_gpToolTip= NULL;
	     }
	
	11. Rebuild the application and bring up the About dialog box, you will see the
	  tooltips.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCmnCtrls kbCtrl kbDlg kbMFC kbToolTip KbUIDesign kbVC210 kbVC220 kbVC400 kbVC500 kbVC600 kbFAQ kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :2.1,2.2,4.0,4.1,4.2,4.2b,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
