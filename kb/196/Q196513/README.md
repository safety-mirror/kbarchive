---
layout: page
title: "Q196513: WD97: How to Simulate WordPerfect's Flush Right Command in Word"
permalink: /kb/196/Q196513/
---

## Q196513: WD97: How to Simulate WordPerfect's Flush Right Command in Word

{% raw %}

	Article: Q196513
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbmacro kbdtacode word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article describes how to create the effect called "flush right" in
	WordPerfect. In WordPerfect, the Flush Right command lines up some text in one
	line with the left margin, and the rest of the text with the right margin. The
	following is an example of this type of formatting:
	
	  Chapter 4                                           Page 72
	  text text text text text text text text text text text text
	  text text text text text text text text text text text text
	  text text text text text text text text text text text text
	
	In Word, you can use a right-aligned tab or a two-column table to accomplish this
	effect. A two-column table is the fastest way to align text in this fashion.
	
	You can set the right-aligned tab manually, or you can create a macro to set the
	tab automatically. If you use this type of formatting only occasionally, or if
	you are interested in learning more about setting tabs, read the "Method 2: Set
	the Right-Aligned Tab Manually" section of this article.
	
	MORE INFORMATION
	================
	
	To simulate the effect of the Flush Right command, use one of the following
	methods.
	
	Method 1: Create a Two-Column Table
	-----------------------------------
	
	1. Place the insertion point on the blank line where you want the text to
	  appear.
	
	2. On the Table menu, click Insert Table. In the Number of Columns box, type "2"
	  (without the quotation marks). In the Number of Rows box, type "1" (without
	  the quotation marks). Click OK.
	
	  The table appears in the document. If you do not see the table, click
	  Gridlines on the Table menu.
	
	3. In the first column, type the text that you want to appear along the left
	  margin.
	
	4. Click the right column. On the Format menu, click Paragraph. On the Indents
	  and Spacing tab, select Right on the Alignment drop-down list.
	
	5. Type the text you want to appear along the right edge of the page.
	
	Method 2: Set a Right-Aligned Tab Manually
	------------------------------------------
	
	1. Click the Show/Hide button on the Standard toolbar so that paragraph marks
	  and spaces are visible.
	
	  This makes it easier to see the tab mark when you insert it in step 4.
	
	2. Click the View menu and make sure that Ruler is selected.
	
	3. Type the text you want to appear along the left margin.
	
	4. Press the TAB key.
	
	  A small arrow (tab indicator) appears next to the text.
	
	5. Move the pointer to the left edge of the ruler. A small black "L" symbol is
	  in a small box. Click the box. Each time you click it, a different symbol
	  appears. Each symbol represents a different type of tab. Click the box until
	  a small backward "L" appears.
	
	6. Move the pointer to the place on the ruler where you want the right edge of
	  the text to appear. (Hint: It may be easiest to see this if you do not click
	  all the way at the right edge of the ruler. Start a little way in from the
	  right edge. You can easily drag the tab setting later.) Click the mouse
	  button.
	
	  A small backward "L" appears on the ruler.
	
	7. Type the text that you want to appear at the right edge.
	
	The text is now aligned along the left and right margins.
	
	When you press ENTER to start a new paragraph, the new paragraph will have the
	same tab setting.
	
	NOTE: If you do not see the same tab setting when you press ENTER, you have the
	WordPerfect options turned on. To disable these options, click Options on the
	Tools menu, select the General tab, and clear the Help for WordPerfect Users and
	the Navigation Keys for WordPerfect Users check boxes.
	
	The third-party products mentioned here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: word perfect wp justify justified justification flush right same lineup ALT+F6 ALT+F7 edge
	
	======================================================================
	Keywords          : kbmacro kbdtacode word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
