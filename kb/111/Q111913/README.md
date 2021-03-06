---
layout: page
title: "Q111913: Creating Comma-Delimited File That Retains Trailing Space"
permalink: /kb/111/Q111913/
---

## Q111913: Creating Comma-Delimited File That Retains Trailing Space

{% raw %}

	Article: Q111913
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.0,2.5,2.5a,2.5b; WINDOWS:2.5,2.5a,2.5b,3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 08-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a, 2.5b 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you are copying a FoxPro database to a comma-delimited file using the COPY
	TO <filename> TYPE DELIMITED command, the trailing blanks of each field
	are removed. Occasionally, the entire file, including any trailing blanks found
	in a field, needs to be copied to an ASCII file, but no options exist for the
	COPY TO command to accomplish this. However, you can use low-level file
	functions to transport the entire contents of every field from a database into a
	comma-delimited ASCII file.
	
	MORE INFORMATION
	================
	
	The following code uses low-level file functions to read the CLIENTS.DBF sample
	database file and place the characters and trailing blanks of each field in a
	comma-delimited ASCII file named TEST.TXT:
	
	     USE C:\Foxprow\Sample\Organize\dbfs\clients.dbf
	     HFILE=FCREATE('c:\Test.txt')
	     GO TOP
	     SCAN
	     =FPUTS(HFILE,Client_id+","+Company+","+Contact+","+Address+;
	     ","+City+","+State+","+Zip+","+Areacode+","+Phone+","+Extension;
	     +","+STR(startbal,8,2)+","+DTOC(Baldate)+Cuisine+","+STR(Type)+",";
	     +Notes)
	     ENDSCAN
	     =FCLOSE(HFILE)
	
	NOTE: By default, the FPUTS() function expects character type data in the fields.
	Therefore, in order to use numeric and date fields, add the STR() and DTOC()
	functions to convert the respective fields to character type data. Adding
	additional parameters to the STR() function preserves the decimal places in the
	numeric fields.
	
	REFERENCES
	==========
	
	"Language Reference," version 2.5, pages L3-528 to L3-530, L3-496, L3-498 to
	L3-499
	
	Additional query words: VFoxWin FoxDos FoxWin spaces padding
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : MS-DOS:2.0,2.5,2.5a,2.5b; WINDOWS:2.5,2.5a,2.5b,3.0
	
	=============================================================================
	

{% endraw %}
