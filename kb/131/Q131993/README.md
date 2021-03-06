---
layout: page
title: "Q131993: PRB: DDX Displays Float/Double in Exponential Format"
permalink: /kb/131/Q131993/
---

## Q131993: PRB: DDX Displays Float/Double in Exponential Format

{% raw %}

	Article: Q131993
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbcode kbnokeyword kbDlg kbMFC kbVC100 kbVC150 kbVC200 kbVC400 kbGrpDSMFCATL
	Last Modified: 29-JUL-2001
	
	1.50 1.51 1.52 | 2.00 2.10 4.00
	WINDOWS        | WINDOWS NT
	kbprb
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, versions 1.5, 1.51, 1.52 
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 2.0, 2.1, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A floating point or double value may appear unexpectedly in exponential format
	(scientific notation) in an edit control in an MFC dialog box or formview. This
	may happen if the following is used to associate a DDX variable of type float or
	double with the edit control:
	
	  DDX_Text(CDataExchange* pDX, int nIDC, float& value)
	  DDX_Text(CDataExchange* pDX, int nIDC, double& value)
	
	This is true even though the documentation indicates that DDX_Text produces the
	exponential format only when the decimal point format is not possible.
	
	CAUSE
	=====
	
	In Visual C++ for Windows version 1.5x and Visual C++ 32-bit Edition, version
	2.x, the edit control value appears in exponential format because DDX_Text()
	uses gcvt() for floats and doubles. The gcvt() C Run-time
	
	  function returns exponential format for all numbers of the format 0.0<x>,
	
	where x is any sequence of digits.
	
	In Visual C++ 32-bit Edition, version 4.0, it is less likely that an edit
	control's value will appear in exponential format, but it is still possible.
	DDX_Text calls the internal C Run-time function _stprintf() with a format
	specifier of "%.*g" and a precision of either FLT_DIG for floats or DBL_DIG for
	doubles. As their underlying implementations are the same, _stprintf() follows
	the same rules as does printf(). As the Visual C++ 4.0 Books Online point out in
	the "printf Type Field Characters" topic, the field type "g" yields a
	
	  Signed value printed in f or e format, whichever is more compact
	  for the given value and precision. The e format is used only when
	  the exponent of the value is less than -4 or greater than or equal
	  to the precision argument. . .
	
	RESOLUTION
	==========
	
	To work around this behavior, rewrite the DDX_Text() function to use fcvt().
	It's a good idea to create a function that calls fcvt() and does all the
	formatting of the string returned from fcvt(). You would call this function from
	your own DDX_Text().
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The definitions for the float and the double versions of DDX_Text can be found
	in the MFC source file DLGFLOAT.CPP in the MFC\SRC subdirectory of the main
	Visual C++ product directory. We recommend that you familiarize yourself with
	these functions and those that they call to obtain a solid understanding of
	their implementations. This will help you rewrite them in the event you decide
	to do so.
	
	The following provides two sample code backbones for the resolution mentioned
	above, one for Visual C++ versions 1.5 through 2.2 and one for Visual C++ 4.0.
	Sample Code I assumes that you have an edit control with ID IDC_EDIT1 on a form
	view with an associated DDX variable of type float called m_eFloat. The custom
	DDX_Text function is called DDX_MyFloatText. It uses the function
	double_to_char, which reads in a double and returns a character string
	representing the double. Sample Code II makes similar assumptions but supports
	an edit control with type double as well. The custom functions are called
	DDX_MyFloatText and DDX_MyDoubleText. They both depend on the internal CRT
	function _stprintf.
	
	Sample Code I - for Visual C++ 16-bit 1.5x and Visual C++ 32-bit 2.x
	--------------------------------------------------------------------
	
	  // include header files.
	  #include <stdio.h>
	  #include <stdlib.h>
	  #include <string.h>
	
	  //............
	  //............
	  //............
	
	  // The function prototypes
	  void AFXAPI DDX_MyFloatText(CDataExchange* pDX, int nIDC,
	                              float& value);
	  char *double_to_char (double number);
	  static BOOL PASCAL NEAR _AfxSimpleFloatParse(const char* pszText,
	                                               double& d);
	
	  //............
	  //............
	  //............
	
	  // Change the DoDataExchange to use DDX_MyFloatText
	  void CDlgfloatView::DoDataExchange(CDataExchange* pDX)
	  {
	      CFormView::DoDataExchange(pDX);
	      //{{AFX_DATA_MAP(CDlgfloatView)
	      DDX_MyFloatText(pDX, IDC_EDIT1, m_eFloat);
	      //}}AFX_DATA_MAP
	  }
	
	  //............
	  //............
	  //............
	
	  // Implementation of DDX_MyFloatText and other helper functions
	  void AFXAPI DDX_MyFloatText(CDataExchange* pDX, int nIDC,
	                              float& value)
	  {
	      HWND hWndCtrl = pDX->PrepareEditCtrl(nIDC);
	      char szT[64];
	      if (pDX->m_bSaveAndValidate)
	      {
	          ::GetWindowText(hWndCtrl, szT, sizeof(szT));
	          double d;
	          if (!_AfxSimpleFloatParse(szT, d))
	          {
	              AfxMessageBox(AFX_IDP_PARSE_REAL);
	              pDX->Fail();            // throws exception
	          }
	          value = (float)d;
	      }
	      else
	      {
	          char * pszCvt = double_to_char(value);
	          if (pszCvt)
	          {
	              int nNewLen = lstrlen(pszCvt);
	              char szOld[64];
	              // fast check to see if text really changes (reduces
	              // flash in controls)
	              if (nNewLen > sizeof(szOld) ||
	                  ::GetWindowText(hWndCtrl, szOld, sizeof(szOld)) !=
	                                  nNewLen ||
	                  lstrcmp(szOld, pszCvt) != 0)
	              {
	                  // change it
	                  ::SetWindowText(hWndCtrl, pszCvt);
	              }
	              delete pszCvt;
	          }
	          else
	          {
	              TRACE("DDX_MyFloatText() failed to convert float
	                    value.\n");
	              pDX->Fail();            // throws exception
	          }
	      }
	  }
	
	  #define PRECISION  5
	
	  char *double_to_char (double number)
	  {
	     char *buffer,*temp ;
	
	     int  decimal_spot,
	          sign,
	          count,
	          current_location = 0,
	          zeropos;
	
	     temp = _fcvt (number, PRECISION, &decimal_spot, &sign) ;
	
	     if (strlen (temp) > PRECISION)
	        buffer = new char[(strlen (temp) + 3)];
	     else
	        buffer = new char[(PRECISION + 3)];
	
	     if (buffer == NULL)
	     {
	        OutputDebugString("Memory allocating attempt has failed in"
	                          "'double_to_char'\n") ;
	        return (NULL) ;
	     }
	
	   /* Add negative sign if required. */ 
	
	     if (sign)
	        buffer [current_location++] = '-' ;
	
	   /* Place decimal point in the correct location. */ 
	
	     if (decimal_spot > 0)
	     {
	        strncpy (&buffer [current_location], temp, decimal_spot) ;
	        buffer [decimal_spot + current_location] = '.' ;
	        strcpy (&buffer [decimal_spot + current_location + 1],
	                        &temp [decimal_spot]) ;
	     }
	     else
	     {
	        buffer [current_location++] = '0';
	        buffer [current_location] = '.' ;
	        for(count = current_location-(1+sign);
	            count<abs(decimal_spot); count++)
	           buffer [count + (current_location+1)] = '0' ;
	        strcpy (&buffer [count + (current_location+1)], temp) ;
	     }
	
	     zeropos = strlen(buffer)-3;
	     if (buffer[zeropos+2] == '0')
	     {
	
	       while (buffer[zeropos--] == '0')
	           buffer[zeropos+2] = '\0';
	
	       if (buffer[zeropos+1] != '.')
	           buffer[zeropos+2] = '\0';
	
	     }
	     return (buffer) ;
	  }
	
	  static BOOL PASCAL NEAR _AfxSimpleFloatParse(const char* pszText,
	                                               double& d)
	  {
	      ASSERT(pszText != NULL);
	      while (*pszText == ' ' || *pszText == '\t')
	          pszText++;
	
	      ASSERT(!::IsDBCSLeadByte(*pszText));
	      char chFirst = pszText[0];
	      d = strtod(pszText, (char**)&pszText);
	      if (d == 0.0 && chFirst != '0')
	          return FALSE;   // could not convert
	      while (*pszText == ' ' || *pszText == '\t')
	          pszText++;
	      ASSERT(!::IsDBCSLeadByte(*pszText));
	
	      if (*pszText != '\0')
	          return FALSE;   // not terminated properly
	
	      return TRUE;
	  }
	
	  Sample Code II - for Visual C++ 32-bit 4.0
	  ------------------------------------------
	
	  //............
	  //............
	  //............
	
	  // The function prototypes
	  void AFXAPI DDX_MyFloatText(CDataExchange* pDX, int nIDC, float& value);
	  void AFXAPI DDX_MyDoubleText(CDataExchange* pDX, int nIDC, double& value);
	  void AFXAPI _MyAfxTextFloatFormat(CDataExchange* pDX, int nIDC,
	                                    void* pData, double value, int nSizeGcvt,
	                                    int nSizeType);
	
	  //............
	  //............
	  //............
	
	  // Change the DoDataExchange to use DDX_MyFloatText or DDX_MyDoubleText
	  void CDlgfloatView::DoDataExchange(CDataExchange* pDX)
	  {
	      CFormView::DoDataExchange(pDX);
	      //{{AFX_DATA_MAP(CDlgfloatView)
	      DDX_MyFloatText(pDX, IDC_EDIT1, m_eFloat);
	      DDX_MyDoubleText(pDX, IDC_EDIT2, m_eDouble);
	      //}}AFX_DATA_MAP
	  }
	
	  //............
	  //............
	  //............
	
	  // Implementation of DDX_MyFloatText, DDX_MyDoubleText and
	  //   _MyAfxTextFloatFormat.
	
	  #include <float.h>
	  #define PRECISION  8
	
	  void AFXAPI DDX_MyFloatText(CDataExchange* pDX, int nIDC, float& value)
	  {
	      _MyAfxTextFloatFormat(pDX, nIDC, &value, value, PRECISION, FLT_DIG);
	  }
	
	  void AFXAPI DDX_MyDoubleText(CDataExchange* pDX, int nIDC, double& value)
	  {
	      _MyAfxTextFloatFormat(pDX, nIDC, &value, value, PRECISION, DBL_DIG);
	  }
	
	  void AFXAPI _MyAfxTextFloatFormat(CDataExchange* pDX, int nIDC,
	                                    void* pData, double value, int nSizeGcvt,
	                                    int nSizeType)
	  {
	      ASSERT(pData != NULL);
	
	      HWND hWndCtrl = pDX->PrepareEditCtrl(nIDC);
	
	          // Make sure your buffer is big enough. Strings returned by
	          // _stprintf() using the "f" specifier tend to be longer
	          // than those returned using the "g" specifier.
	      TCHAR szBuffer[64];
	
	      if (pDX->m_bSaveAndValidate)
	      {
	          ::GetWindowText(hWndCtrl, szBuffer, _countof(szBuffer));
	          double d;
	          if (!AfxSimpleFloatParse(szBuffer, d))
	          {
	              AfxMessageBox(AFX_IDP_PARSE_REAL);
	              pDX->Fail();            // throws exception
	          }
	          if (nSizeType == FLT_DIG)
	              *((float*)pData) = (float)d;
	          else
	              *((double*)pData) = d;
	      }
	      else
	      {
	          _stprintf(szBuffer, _T("%.*f"), nSizeGcvt, value);
	          AfxSetWindowText(hWndCtrl, szBuffer);
	      }
	  }
	
	Additional query words: 1.50 2.00 2.10 4.00
	
	======================================================================
	Keywords          : kbcode kbnokeyword kbDlg kbMFC kbVC100 kbVC150 kbVC200 kbVC400 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
