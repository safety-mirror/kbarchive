---
layout: page
title: "Q168447: PRB: DAO SetParamValue Limited to 255 Characters"
permalink: /kb/168/Q168447/
---

## Q168447: PRB: DAO SetParamValue Limited to 255 Characters

{% raw %}

	Article: Q168447
	Product(s): Microsoft C Compiler
	Version(s): 4.0 4.1 4.2 5.0 6.0
	Operating System(s): 
	Keyword(s): kbcode kberrmsg kbDAOsearch kbDatabase kbMFC kbVC kbVC400 kbVC410 kbVC420 kbVC500 kbVC6
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The execution of a query following a call to CDaoQueryDef::SetParamValue()
	results in an error similar to the following:
	
	  
	
	  DAO Call Failed.
	      m_pDAOQueryDef->Execute(COleVariant((long)nOptions))
	      In file daocore.cpp on line 2880
	      scode = 800A0BC9
	
	  Error Code = 3017
	  Source = DAO.QueryDef
	  Description = The size of a field is too long.
	
	CAUSE
	=====
	
	Parameter values are limited to 255 characters.
	
	RESOLUTION
	==========
	
	Do not call SetParamValue with a value that contains more than 255 characters.
	If you need to update or insert a record that does contain long data, use a
	recordset rather than a querydef.
	
	MORE INFORMATION
	================
	
	DAO and the Jet Engine restrict parameter values to 255 characters or less; this
	is not a limitation of the MFC DAO classes.
	
	Sample Code
	-----------
	
	  /* Compile options needed: none
	  */ 
	      CDaoDatabase db;
	      CDaoQueryDef query( &db );
	      int idx;
	      CByteArray blob;
	      const int SIZE = 255;    // Execute will succeed if 255, fail if 256
	      try
	      {
	          db.Open( "C:\\DB1.mdb" );
	          query.Open( "Query1" );
	          query.SetParamValue( "theID", COleVariant( (long)1, VT_I4 ) );
	
	          blob.SetSize( SIZE );
	          for( idx = 0; idx < SIZE; ++idx )
	              blob.SetAt( idx, (BYTE)idx );
	          query.SetParamValue( "theBlob", COleVariant( blob ) );
	          query.Execute();
	      }
	      catch( CDaoException* e )
	      {
	          AfxMessageBox( e->m_pErrorInfo->m_strDescription,
	              MB_ICONEXCLAMATION );
	          e->Delete();
	      }
	      query.Close();
	      db.Close();
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kberrmsg kbDAOsearch kbDatabase kbMFC kbVC kbVC400 kbVC410 kbVC420 kbVC500 kbVC600 kbprb 
	Technology        : kbAudDeveloper kbMFC
	Version           : 4.0 4.1 4.2 5.0 6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
