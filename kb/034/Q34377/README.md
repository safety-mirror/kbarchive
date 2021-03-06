---
layout: page
title: "Q34377: How to Implement a Function Pointer in MASM"
permalink: /kb/034/Q34377/
---

## Q34377: How to Implement a Function Pointer in MASM

{% raw %}

	Article: Q34377
	Product(s): Microsoft Macro Assembler
	Version(s): 5.0,5.1,5.1a,6.0,6.0a,6.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 5.0, 5.1, 5.1a, 6.0, 6.0a, 6.0b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following sample program illustrates how to implement a function pointer
	using the Microsoft Macro Assembler. It takes the address of the function (in
	this example, the address is loaded into ES:DX) and moves it into a 4-byte
	variable; it then does a far call through the pointer.
	
	In this example, it may seem odd to call a function in this manner because the
	function is defined locally and its name is known; however, what if the name of
	the function was not known? What if you were programming a device driver and all
	that was know was the entry point of the function? Using the following
	technique, a name could be given to the address of the function and the function
	could be called like any other function.
	
	MORE INFORMATION
	================
	
	This program illustrates how to implement a function pointer in MASM. This code
	is similar to the code that the C compiler would generate for a C program that
	used a pointer to a function.
	
	Sample Code
	-----------
	
	  ; Assemble options needed: none
	
	     .model small
	
	     .data
	  fptr dd 1 dup(?)   ; set aside four bytes for function address
	
	     .code
	  ;
	  ;  MACRO Definitions
	  ;
	  FARCALL MACRO func_ptr
	     CALL dword ptr func_ptr  ; call by 4-byte far function reference
	     ENDM
	
	  DosExit MACRO
	     MOV  ax, 4C00h    ; ah = 4Ch ( dos exit interrupt) al = 0
	     INT  21h
	     ENDM
	  ;
	  ;  FUNCTION Definition: function uses int 10h, function 07h to
	  ;                       initialize a window
	  ;
	     PUBLIC _ClrScr
	
	  _ClrScr PROC FAR
	
	     PUSH bp          ; save bp
	     MOV  bp, sp      ; get sp
	     PUSH bx          ; save registers
	     PUSH cx
	     PUSH dx
	
	     MOV ax, 0700h    ; ah = 7,  al = 0
	     MOV bx, 0700h    ; bh = 7,  bl = 0
	     XOR cx, cx       ; cx = 0
	     MOV dx, 184Fh    ; dh = 24, dl = 79, decimal
	     INT 10h
	
	     MOV ax, 0200h    ; ah = 2, al = 0
	     XOR bx, bx       ; bx = 0
	     XOR dx, dx       ; dx = 0
	     INT 10h
	
	     XOR  ax, ax      ; function returns void
	     POP  dx          ; restore registers
	     POP  cx
	     POP  bx
	
	     MOV  sp, bp      ; reset sp
	     POP  bp          ; restore bp
	     RET              ; return
	   _ClrScr ENDP
	
	  BEGIN:              ; main part of the program
	  ;
	  ;  Get address of the function, put in es:dx
	  ;
	     mov  dx, SEG _ClrScr
	     mov  es, dx
	     mov  dx, OFFSET _ClrScr
	  ;
	  ;  Load function address into fptr
	  ;
	     mov  WORD PTR fptr, dx    ; low word of fptr is the
	                               ; offset of the function
	     mov  WORD PTR fptr+2, es  ; high word of fptr is the
	                               ; segment of the function
	  ;
	  ;  Call the function via a function pointer
	  ;
	     FARCALL fptr              ; call function. FARCALL is a macro
	                               ; defined above
	  ;
	  ;  Exit to DOS
	  ;
	     DosExit                   ; Exit to DOS. DosExit is a macro
	                               ; defined above
	
	     END BEGIN
	
	Additional query words: kbinf 5.00 5.10 5.10a 6.00 6.00a 6.00b
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM510 kbMASM600 kbMASM500 kbMASM600a kbMASM510a kbMASM600b
	Version           : :5.0,5.1,5.1a,6.0,6.0a,6.0b
	
	=============================================================================
	

{% endraw %}
