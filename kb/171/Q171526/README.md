---
layout: page
title: "Q171526: FIX: Setting Enabled=False for TreeView Causes Paint Problems"
permalink: /kb/171/Q171526/
---

## Q171526: FIX: Setting Enabled=False for TreeView Causes Paint Problems

{% raw %}

	Article: Q171526
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The TreeView Control does not paint correctly when the Enabled Property is set
	to False. When the TreeView Enabled Property is set to False, the "text areas"
	for each visible node should be painted in a highlight color. Instead, the "text
	areas" are painted with one color and the lines leading to the "text areas" are
	painted a different shade.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 2.
	
	For more information on the Visual Studio 97 Service Pack 2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where,and Why
	
	For a list of the Visual Basic 5.0 bugs that were fixed in the Visual Studio 97
	Service Pack 2, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q171554 INFO: Visual Basic 5.0 Fixes in Visual Studio 97 Service Pack 2
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a New Standard EXE Project.
	
	2. Click Components on the Project menu.
	
	3. From the Controls Tab in the Components Dialog box check "Microsoft Windows
	  Common Controls 5.0" and click OK.
	
	4. Add a CommandButton and a TreeView Control to Form1.
	
	5. Add the following code to Form1:
	
	        Private Sub Command1_Click()
	          TreeView1.Enabled = Not TreeView1.Enabled
	        End Sub
	
	        Private Sub Form_Load()
	          TreeView1.LineStyle = tvwRootLines
	          'Add Node objects.
	          Dim nodX As Node    ' Declare Node variable.
	          'First node with 'Root' as text.
	          Set nodX = TreeView1.Nodes.Add(, , "r", "Root")
	
	          'Create three child Nodes of Node 1 ("Root").
	          Set nodX = TreeView1.Nodes.Add("r", tvwChild, "child1","Child")
	
	          Set nodX = TreeView1.Nodes.Add("r", tvwChild, "child2","Child")
	
	          Set nodX = TreeView1.Nodes.Add("r", tvwChild, "child3","Child")
	
	        End Sub
	
	6. Run the project by pressing the F5 key.
	
	7. Expand the Nodes on the TreeView and then click the CommandButton to change
	  the Enabled property of the TreeView control.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
