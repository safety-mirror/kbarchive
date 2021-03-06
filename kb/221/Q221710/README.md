---
layout: page
title: "Q221710: FIX: Component Gallery Dynamic Folder for Web View Won't Refresh"
permalink: /kb/221/Q221710/
---

## Q221710: FIX: Component Gallery Dynamic Folder for Web View Won't Refresh

{% raw %}

	Article: Q221710
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbInternet kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix kbGrpDSFox kbDSupport
	Last Modified: 01-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After making a change to the Properties tab of a dynamic folder in the Component
	Gallery, the Web page the folder points to is not refreshed. You must click on
	the folder in the left-hand pane of the Component Gallery to force a refresh.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3.
	
	For more information about Visual Studio service packs, please see the following
	articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Open the Component Gallery.
	
	2. Click the Options toolbar button and make sure the Advanced Editing Enabled
	  check box is selected.
	
	3. Click the Visual FoxPro Catalog in the left-hand pane of the Component
	  Gallery.
	
	4. Right-click in the right-hand pane and choose New Item and Folder.
	
	5. In the left-hand pane, right-click the New folder and choose Properties.
	  Select the Node tab, type the following in the Dynamic folder text box, and
	  click OK:
	
	  "http://www.microsoft.com" (without the quotation marks)
	
	6. Right-click the New folder and choose Properties. Change the name in the Name
	  text box to some other value and click OK.
	
	Note that the folder name changes, but the Web page is not refreshed. You must
	click on the folder to force a refresh.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbInternet kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix kbGrpDSFox kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
