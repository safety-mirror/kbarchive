---
layout: page
title: "Q191235: HOWTO: Use the Shared Property Manager in MTS Through VB Code"
permalink: /kb/191/Q191235/
---

## Q191235: HOWTO: Use the Shared Property Manager in MTS Through VB Code

{% raw %}

	Article: Q191235
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When writing components that run under the control of Microsoft Transaction
	Server (MTS), the Shared Property Manager (SPM) gives components a way to store
	and share "stateful" information. For objects to share state, they all must be
	running in the same server process with the Shared Property Manager.
	
	This article demonstrates how to use Visual Basic code to set and retrieve a
	property in the Shared Property Manager. This article assumes that you are
	already familiar with MTS and writing ActiveX dlls that run under the control of
	MTS.
	
	For more information on writing applications in Visual Basic that use MTS, please
	see the following article in the Microsoft Knowledge Base:
	
	  Q186342 : HOWTO: Create a Simple 3-Tier App Using VB, MTS, and SQL Server
	
	MORE INFORMATION
	================
	
	The are three basic steps in this article:
	
	1. Create the Visual Basic ActiveX DLL which will contain the methods that set
	  and retrieve the SPM property.
	
	2. Create a simple client that will access this component.
	
	3. Install the component into MTS.
	
	NOTE: This article assumes that the development of the component and client
	mentioned above will be done on the same machine as MTS.
	
	Step 1: Create the ActiveX DLL
	------------------------------
	
	1. Create a new Visual Basic ActiveX DLL project.
	
	2. From the Project menu, choose Project Properties. On the General tab, change
	  the project name to "SPMSample," check the Unattended Execution box, and make
	  sure the threading model is set to Apartment Threading.
	
	3. From the Project menu, choose References. Add a reference to Microsoft
	  Transaction Server Type Library and Shared Property Manager Type Library.
	
	4. Add the following code to the default class:
	
	        Option Explicit
	
	        Public Function GetSPM(ByVal szGroup As String, _
	                                ByVal szProperty As String) _
	                                As String
	
	            On Error GoTo ErrHandler
	
	            Dim ctxObject As ObjectContext
	            Dim spmMgr As SharedPropertyGroupManager
	            Dim spmGroup As SharedPropertyGroup
	            Dim spmProp As SharedProperty
	            Dim bGroupExists As Boolean
	            Dim bPropExists As Boolean
	
	            Set ctxObject = GetObjectContext()
	
	            Set spmMgr = CreateObject _
	                ("MTxSpm.SharedPropertyGroupManager.1")
	
	            'OPTIONS
	            '-------------------------------------------------
	            'LockSetGet (0)  = Locks the particular property
	            '                   while it is being set
	            'LockMethod (1) = Locks all of the properties
	            '                   in the property group
	            '                   until the method is complete
	            '
	            'Standard (0) = Destroys property when all
	            '               clients have released there reference
	            'Process (1) = The property group is not destroyed
	            '               until the process in which it lives
	            '               is terminated.
	            '
	            'NOTE: If debugging these from within the VB 5.0 IDE
	            'then you will need to use LockSetGet.  LockMethod
	            'requires that the object have an ObjectContext
	            '-------------------------------------------------
	            'Set spmGroup = spmMgr.CreatePropertyGroup _
	                (Trim(szGroup), LockSetGet, Process, bGroupExists)
	            Set spmGroup = spmMgr.CreatePropertyGroup _
	                (Trim(szGroup), LockMethod, Process, bGroupExists)
	            Set spmProp = spmGroup.CreateProperty _
	                (Trim(szProperty), bPropExists)
	
	            If bPropExists = False Then
	                GetSPM = "Property Does Not Exist"
	            Else
	                GetSPM = spmProp.Value
	            End If
	
	            ctxObject.SetComplete
	            Exit Function
	
	        ErrHandler:
	
	            If Not ctxObject Is Nothing Then
	                ctxObject.SetAbort
	            End If
	            GetSPM = "Error Occurred"
	            Err.Raise Err.Number, "", Err.Description, ""
	            Exit Function
	
	        End Function
	
	        Public Sub SetSPM(ByVal szGroup As String, _
	                            ByVal szProperty As String, _
	                            ByVal szValue As String)
	
	            On Error GoTo ErrHandler
	
	            Dim ctxObject As ObjectContext
	            Dim spmMgr As SharedPropertyGroupManager
	            Dim spmGroup As SharedPropertyGroup
	            Dim spmProp As SharedProperty
	            Dim groupExists As Boolean
	            Dim propExists As Boolean
	
	            Set ctxObject = GetObjectContext()
	
	            'Create an instance of the SPM.  Retrieve the
	            'group and property and then set the value
	            '-------------------------------------------------
	            Set spmMgr = CreateObject _
	                ("MTxSpm.SharedPropertyGroupManager.1")
	            Set spmGroup = spmMgr.CreatePropertyGroup _
	                (Trim(szGroup), LockSetGet, Process, groupExists)
	            'Set spmGroup = spmMgr.CreatePropertyGroup _
	                (Trim(szGroup), LockMethod, Process, groupExists)
	            Set spmProp = spmGroup.CreateProperty _
	                    (Trim(szProperty), propExists)
	
	            spmProp.Value = szValue
	
	            ctxObject.SetComplete
	            Exit Sub
	
	        ErrHandler:
	
	            If Not ctxObject Is Nothing Then
	                ctxObject.SetAbort
	            End If
	            Err.Raise Err.Number, "", Err.Description, ""
	            Exit Sub
	
	        End Sub
	
	Step 2: Create the Client Application
	-------------------------------------
	
	1. Create a new Visual Basic Standard EXE file. Form1 is created by default.
	
	2. On the default form, add one Label, one Text Box, and two CommandButtons.
	
	3. Add the following code to the default form:
	
	        Private Sub Command1_Click()
	
	            Dim obj As Object
	            Dim szGroup As String
	            Dim szProperty As String
	            Dim szValue As String
	
	            szValue = Trim(Text1.Text)
	
	            szGroup = "TestGroup"
	            szProperty = "TestProperty"
	            Set obj = CreateObject("SPMSample.Class1")
	
	            obj.SetSPM szGroup, szProperty, szValue
	
	            Set obj = Nothing
	
	        End Sub
	
	        Private Sub Command2_Click()
	
	            Dim obj As Object
	            Dim szGroup As String
	            Dim szProperty As String
	            Dim szValue As String
	
	            szValue = Trim(Text1.Text)
	
	            szGroup = "TestGroup"
	            szProperty = "TestProperty"
	            Set obj = CreateObject("SPMSample.Class1")
	
	            Label1.Caption = obj.GetSPM(szGroup, szProperty)
	
	            Set obj = Nothing
	
	        End Sub
	
	        Private Sub Form_Load()
	
	            Command1.Caption = "Set SPM Value"
	            Command2.Caption = "Retrieve SPM Value"
	
	        End Sub
	
	Step 3: Install the Component into MTS
	--------------------------------------
	
	1. Start the Microsoft Management Console (MMC), Transaction Server Explorer.
	
	2. Using the Tree View in the left-hand pane, expand "Computers," then "My
	  Computer," and then the "Packages Installed" node.
	
	3. Right-mouse click the Packages Installed icon and choose "New," and then
	  "Package."
	
	4. Choose to create and empty package. Name the package "SPMSample" and have it
	  run as the interactive user.
	
	5. Select the Components folder under the newly-created package, right- mouse
	  click and choose "New," and then choose "Component."
	
	6. Choose 'Import component(s) that are already registered' and choose
	  SPMSample.Class1 from the list that is displayed.
	
	You should now be able to run your client application and set and retrieve the
	Shared Property Manager value.
	
	NOTE: It is assumed here that the client will be run on the same machine as MTS.
	
	REFERENCES
	==========
	
	MTS 2.0 Help File
	
	  Q186342 : HOWTO: Create a Simple 3-Tier App Using VB, MTS, and SQL Server
	
	Additional query words: SPM kbMTS kbVBp500 kbVBp600 kbdse kbDSupport kbVBp kbActiveX
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
