---
layout: page
title: "Q59928: Error R6001 Generated by Compiler in Huge Model"
permalink: /kb/059/Q59928/
---

## Q59928: Error R6001 Generated by Compiler in Huge Model

{% raw %}

	Article: Q59928
	Product(s): See article
	Version(s): 2.00 2.01
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist2.00 buglist2.01 fixlist2.50 fixlist2.51 | mspl13_c
	Last Modified: 15-APR-1990
	
	When casting the result of pointer arithmetic to either a double or a
	float, QuickC Version 2.00 or QuickAssembler Version 2.01 may produce
	the following error when compiling in the huge model:
	
	   run-time error R6001
	   - null pointer assignment
	
	This error occurs in the huge memory model only. Turning off all
	optimizations using the /Od switch does not help.
	
	The compiler does produce an OBJ file, but this file is not valid. If
	an attempt is made to link this OBJ into an executable, the following
	error will be issued by the linker:
	
	   xxx.obj (xxx.c) : error L2029 : '__' : unresolved external
	
	The following code reproduces the error:
	
	void main(void)
	{
	        char * foo = "abcdef",
	             * bar = foo + 5 ;
	        double dbl;
	
	        dbl = (double) (foo-bar) ;
	}
	
	Substituting "float" for "double" produces the same error.
	
	In memory models other than huge, this same situation generates the
	following error message:
	
	   fatal error C1001: Internal Compiler Error
	   (compiler file 'gencode.c', line 389)
	   Contact Microsoft Product Support
	
	For more information, query on the following words:
	
	   ICE and error and casting and pointer and arithmetic
	
	Workaround
	----------
	
	The problem can be solved by using a temporary variable of type long to
	store the result of the pointer arithmetic. The temporary variable
	used to store the result of the pointer arithmetic is of type long
	because all huge pointer arithmetic is done using 4-byte signed (that
	is, long) arithmetic.
	
	The following is the same as the above example, but uses a temporary
	variable:
	
	void main(void)
	{
	        char * foo = "abcdef",
	             * bar = foo + 5 ;
	        double dbl ;
	        long   temp ;
	
	        temp = foo-bar ;
	        temp = (double) temp ;
	}
	
	Microsoft has confirmed this to be a problem with QuickC Version 2.00
	and QuickAssembler Version 2.01. It has been corrected in QuickC
	Version 2.50 and Quick Assembler 2.51.

{% endraw %}
