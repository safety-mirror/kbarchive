---
layout: page
title: "Q121109: WD97: Font Changes During Mail Merge"
permalink: /kb/121/Q121109/
---

## Q121109: WD97: Font Changes During Mail Merge

{% raw %}

	Article: Q121109
	Product(s): Word 97 for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbfield word97 kbmerge
	Last Modified: 06-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you perform a mail merge, the merged information may be printed in a
	different font. This behavior occurs when the default Normal style is different
	from the font applied to your mail merge main document.
	
	For example, if you choose Courier as the default font for your Normal style but
	decide to format the main document using Arial, your text will be printed in
	Arial, but the merged fields will be printed in a Courier font.
	
	WORKAROUND
	==========
	
	To work around this problem, use the method appropriate for your situation.
	
	Method 1: Add the Charformat switch
	-----------------------------------
	
	Edit the merge field and add the \*Charformat switch. To edit the merge field,
	follow these steps:
	
	1. Place the insertion point in the merge field.
	
	2. Press SHIFT+F9 to view the field code.
	
	3. Move the insertion point to the left of the right bracket (}).
	
	4. Type "\*Charformat" (without the quotation marks).
	
	  NOTE: If the word "mergeformat" appears in this field, delete it and replace
	  it with the word "Charformat" (without the quotation marks).
	
	5. Select the first character within the field brace. Make sure that this
	  character is set to the font and font size that you desire. If it is not,
	  change it to the desired font and font size.
	
	6. Press SHIFT+F9 to show the result of the field code.
	
	The field will not look any different than it did before, but when you perform
	the merge, the correct font will be used.
	
	Method 2: Change the Normal Style
	---------------------------------
	
	You can modify the built-in Normal style to match the font desired. To change the
	Normal style, follow these steps:
	
	1. Open your mail merge main document.
	
	2. On the Format menu, click Style.
	
	3. In the Style dialog box, under Styles, select Normal and then click Modify.
	
	4. In the Modify Style dialog box, click Format and then click Font.
	
	  NOTE: If you want your changes to be made permanent and applied to all new
	  documents, click to select the "Add to template" check box.
	
	5. On the Font tab, change the Font to the desired font you want your mail merge
	  documents to merge with, and then click OK to close the Font dialog box.
	
	  NOTE: On the Font tab, make any other changes to the font, as desired.
	
	6. Click OK to close the Modify Style dialog box, and then click Close to close
	  the Style dialog box.
	
	Method 3: Merge to a New Document and Make Formatting Changes
	-------------------------------------------------------------
	
	To merge to a new document and make formatting changes, follow these steps:
	
	1. Perform your mail merge to a new document.
	
	2. In the merged document, on the Edit menu, click Select All.
	
	3. On the Format menu, click Font.
	
	4. On the Font tab, select the desired font for your merged document and then
	  click OK.
	
	  NOTE: On the Format tab, make any other changes to the font as desired.
	
	When you print your merged document, all of the text will now be printed using
	the desired font.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	Additional query words: font change typeface different differs mail merge print data fonts
	
	======================================================================
	Keywords          : kbfield word97 kbmerge 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : :
	
	=============================================================================
	

{% endraw %}
