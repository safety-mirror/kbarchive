---
layout: page
title: "Q162613: HOWTO: Manipulate Icons in the System Tray with Visual Basic"
permalink: /kb/162/Q162613/
---

## Q162613: HOWTO: Manipulate Icons in the System Tray with Visual Basic

{% raw %}

	Article: Q162613
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbOSWin95 kbOSWin98 kbGrpDSVB kbDSupport kb
	Last Modified: 26-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	One of the new features of the Windows 95, Windows 98, Windows Me, Windows NT
	4.0, and Windows 2000 user interface is the taskbar status area. This article
	demonstrates how to use Visual Basic to add, modify, and delete status or
	notification indicators in the taskbar status area.
	
	MORE INFORMATION
	================
	
	The taskbar status area is located to the right of the Start button, and
	provides you with status or notification indicators about your programs. Icons
	with ToolTips are typically used as indicators in the taskbar status area. The
	following are some examples of how to use the taskbar status area:
	
	- You can adjust the consumption level of your laptop's batteries by clicking a
	  vertical graph in the taskbar status area and adjusting it in the window that
	  appears. The graph indicates the amount of power left in your laptop
	  computer's batteries.
	
	- You can track your favorite stock by creating an icon that changes when your
	  stock changes price. Click the icon to display a chart of the stock.
	
	- You can adjust the volume control on a multimedia device by clicking the icon
	  and displaying more controls.
	
	To manipulate an icon in the taskbar status area, use the Windows API function
	Shell_NotifyIcon in the Shell32.dll file. This function allows you to add,
	modify, delete, set a ToolTip string, and send a callback message to execute
	mouse events. Visual Basic versions 4.0 and earlier do not directly accept
	callback messages or functions. However, there are three ways to work around
	this limitation:
	
	1. The Hard Way: Create a control that accepts callbacks. Refer to the Microsoft
	  Systems Journal article cited in the References section of this article for a
	  way to create a control that accepts callbacks. To create this control, you
	  need Visual C++.
	
	2. The Easy Way: Use a third-party control that intercepts messages, such as the
	  Message Blaster control.
	
	3. The Simple Way: Use a Visual Basic intrinsic control to serve as a Window
	  that reacts to the callback message. This article contains a sample program
	  that uses this method. With this method, you want to use an event in a
	  control that is rarely used. The event will be exclusively used to process
	  the callback message.
	
	In Visual Basic 5.0 and later, you can use the AddressOf Operator to call
	callback functions.
	
	The next section explains the Shell_NotifyIcon function and the requirements to
	use this function.
	
	Shell_NotifyIcon Function
	-------------------------
	
	You use the Shell_NotifyIcon function to send a message to a system to add,
	modify, or delete an icon from the taskbar status area. The function returns
	True if the message is sent successfully or False if the function is
	unsuccessful. The arguments of the functions are as follows:
	
	  dwMessage: A message to execute an action. This parameter can be one of
	  the following values:
	
	     NIM_ADD: Adds an icon to the status area.
	     NIM_DELETE: Deletes an icon from the status area.
	     NIM_MODIFY: Modifies an icon in the status area.
	
	  The values of these messages can be found in the header file,
	  Shellapi.h.
	
	  pnid: A pointer to a NOTIFYICONDATA structure. To pass this argument to
	  the function, create a user-defined data type called NOTIFYICONDATA
	  (shown later in this section) and pass this data type by value.
	
	The NOTIFYICONDATA structure contains the following elements:
	
	  cbSize: Passes the size of the NOTIFYICONDATA data type.
	     Data Type: Long.
	     Value: Use the Len function with the variable declared as this data
	     type as the argument.
	
	  hWnd: Handle of the window used to receive the notification message.
	     Data Type: Long.
	     Value: The hWnd property of the control used to receive this message.
	
	  uId: Identifier of the icon in the status area.
	     Data Type: Long.
	     Value: Any value within the limits of the Long data type. The sample
	     program uses vbNull.
	
	  uFlags: Array of flags that indicate which of the other members contain
	  valid data.
	     Data Type: Long.
	     Value: Any combination of the following constants to indicate that
	     the member of this structure is valid and will be used:
	
	        NIF_ICON: Passing this flag indicates that the value for the
	        hIcon will be the icon that appears in the taskbar status area.
	
	        NIF_MESSAGE: Passing this flag indicates that the uCallBackMessage
	        value will be used as the callback message.
	
	        NIF_TIP: Passing this flag indicates that the value of szTip will
	        be used as the ToolTip for the icon in the taskbar status area.
	
	  uCallBackMessage: Identifier of the notification message sent to the
	  window that is used to receive the messages.
	     Data Type: Long.
	     Value: The message used to identify that a mouse event has occurred
	     within the rectangular boundaries of the icon in the taskbar status
	     area.
	
	  hIcon: Handle of the icon that is displayed in the taskbar status area.
	     Data Type: Long.
	     Value: The image that will be used as an icon in the taskbar status
	     area. This can be the icon property of a control, an image from an
	     image control, or any icon image.
	
	  szTip: String to be used as the ToolTip text.
	     Data Type: Fixed-length string 64 bytes long.
	     Value: Any null-terminated string under 64 bytes.
	
	The next section explains how to use this function in a sample program to
	manipulate icons in the taskbar status area.
	
	The Sample Program
	------------------
	
	The sample program consists of a form containing two command buttons and the
	common dialog box control. When you click Add Icon, you set the values of the
	NOTIFYICONDATA data type. In this data type, you set the following values:
	
	  cbSize: The length of the variable that uses the Len function.
	
	  hWnd: The handle of the window used to receive the callback messages. In
	  the sample program, the form is used as the window to receive the
	  messages.
	
	  uId: The icon identifier. Although you can use any number, the sample
	  program uses the vbNull constants.
	
	  uFlags: Array flags indicate what members of this structure are valid.
	  The sample program uses all the flags for maximum versatility.
	
	  uCallBackMessage: The message that is sent when mouse activity occurs on
	  the icon in the taskbar status tray. The mouse message that is sent maps
	  to a mouse event in the control specified in the hWnd value. You should
	  use a mouse message that can handle the messages exclusively. For
	  example, the sample program uses the WM_MOUSEMOVE message because this
	  message maps to the MouseMove event of the form. Rarely used in its
	  intended form, the MouseMove event is a suitable event for this purpose.
	
	  hIcon: The icon that is to be displayed in the taskbar status area. The
	  sample program uses the form icon.
	
	  szTip: The ToolTip string. The string must be terminated with a null
	  character so the vbNullChar constant is concatenated to the string.
	
	After setting the data, you then call the Shell_NotifyIcon function and pass the
	NOTIFYICONDATA along with a message to add the icon to the taskbar status area.
	
	When you pass the mouse pointer over the icon in the taskbar status area, the
	form receives the message WM_MOUSEMOVE. This message maps to the form's
	MouseMove event. The X argument is the product of one of the mouse constants
	that indicates the mouse input (such as a left-click, right-click, single-click,
	or double-click) and the TwipsPerPixelX property of the screen. The mouse input
	is produced by dividing the X argument with this property. The mouse input is
	then used in a Select Case statement to execute a series of instructions.
	
	For example, when you double-click the icon, the common dialog box appears and
	allows you to select a different icon. The hIcon value of the NOTIFYICONDATA
	data type is changed to the new icon. The Shell_NotifyIcon function is called
	with the new data type and a message to modify the icon in the taskbar status
	area.
	
	If you right-click the icon, you execute the InputBox function that changes the
	ToolTip text. The new string is null terminated with the vbNullChar constant and
	the szTip value is changed to the new string. The Shell_NotifyIcon function is
	called with the new NOTIFYICONDATA data and a message to modify the icon.
	
	When you click Delete Icon or exit the application, the Shell_NotifyIcon function
	is called with a message to delete the icon.
	
	Steps To Create Sample Program
	------------------------------
	
	1. Start Visual Basic. If it is already running, go to the File menu and click
	  New Project.
	
	2. Place two CommandButtons and a common dialog box control on Form1.
	
	3. Copy the following code to the Form1 code window:
	
	        'Declare a user-defined variable to pass to the Shell_NotifyIcon
	        'function.
	        Private Type NOTIFYICONDATA
	           cbSize As Long
	           hWnd As Long
	           uId As Long
	           uFlags As Long
	           uCallBackMessage As Long
	           hIcon As Long
	           szTip As String * 64
	        End Type
	
	        'Declare the constants for the API function. These constants can be
	        'found in the header file Shellapi.h.
	
	        'The following constants are the messages sent to the
	        'Shell_NotifyIcon function to add, modify, or delete an icon from the
	        'taskbar status area.
	        Private Const NIM_ADD = &H0
	        Private Const NIM_MODIFY = &H1
	        Private Const NIM_DELETE = &H2
	
	        'The following constant is the message sent when a mouse event occurs
	        'within the rectangular boundaries of the icon in the taskbar status
	        'area.
	        Private Const WM_MOUSEMOVE = &H200
	
	        'The following constants are the flags that indicate the valid
	        'members of the NOTIFYICONDATA data type.
	        Private Const NIF_MESSAGE = &H1
	        Private Const NIF_ICON = &H2
	        Private Const NIF_TIP = &H4
	
	        'The following constants are used to determine the mouse input on the
	        'the icon in the taskbar status area.
	
	        'Left-click constants.
	        Private Const WM_LBUTTONDBLCLK = &H203   'Double-click
	        Private Const WM_LBUTTONDOWN = &H201     'Button down
	        Private Const WM_LBUTTONUP = &H202       'Button up
	
	        'Right-click constants.
	        Private Const WM_RBUTTONDBLCLK = &H206   'Double-click
	        Private Const WM_RBUTTONDOWN = &H204     'Button down
	        Private Const WM_RBUTTONUP = &H205       'Button up
	
	        'Declare the API function call.
	        Private Declare Function Shell_NotifyIcon Lib "shell32" _
	           Alias "Shell_NotifyIconA" _
	           (ByVal dwMessage As Long, pnid As NOTIFYICONDATA) As Boolean
	
	        'Dimension a variable as the user-defined data type.
	        Dim nid As NOTIFYICONDATA
	
	        Private Sub Command1_Click()
	           'Click this button to add an icon to the taskbar status area.
	
	           'Set the individual values of the NOTIFYICONDATA data type.
	           nid.cbSize = Len(nid)
	           nid.hWnd = Form1.hWnd
	           nid.uId = vbNull
	           nid.uFlags = NIF_ICON Or NIF_TIP Or NIF_MESSAGE
	           nid.uCallBackMessage = WM_MOUSEMOVE
	           nid.hIcon = Form1.Icon
	           nid.szTip = "Taskbar Status Area Sample Program" & vbNullChar
	
	           'Call the Shell_NotifyIcon function to add the icon to the taskbar
	           'status area.
	           Shell_NotifyIcon NIM_ADD, nid
	        End Sub
	
	        Private Sub Command2_Click()
	           'Click this button to delete the added icon from the taskbar
	           'status area by calling the Shell_NotifyIcon function.
	           Shell_NotifyIcon NIM_DELETE, nid
	        End Sub
	
	        Private Sub Form_Load()
	           'Set the captions of the command button when the form loads.
	           Command1.Caption = "Add an Icon"
	           Command2.Caption = "Delete Icon"
	        End Sub
	
	        Private Sub Form_Terminate()
	           'Delete the added icon from the taskbar status area when the
	           'program ends.
	           Shell_NotifyIcon NIM_DELETE, nid
	        End Sub
	
	        Private Sub Form_MouseMove _
	           (Button As Integer, _
	            Shift As Integer, _
	            X As Single, _
	            Y As Single)
	            'Event occurs when the mouse pointer is within the rectangular
	            'boundaries of the icon in the taskbar status area.
	            Dim msg As Long
	            Dim sFilter As String
	            msg = X / Screen.TwipsPerPixelX
	            Select Case msg
	               Case WM_LBUTTONDOWN
	               Case WM_LBUTTONUP
	               Case WM_LBUTTONDBLCLK
	               CommonDialog1.DialogTitle = "Select an Icon"
	               sFilter = "Icon Files (*.ico)|*.ico"
	               sFilter = sFilter & "|All Files (*.*)|*.*"
	               CommonDialog1.Filter = sFilter
	               CommonDialog1.ShowOpen
	               If CommonDialog1.filename <> "" Then
	                  Form1.Icon = LoadPicture(CommonDialog1.filename)
	                  nid.hIcon = Form1.Icon
	                  Shell_NotifyIcon NIM_MODIFY, nid
	               End If
	               Case WM_RBUTTONDOWN
	                  Dim ToolTipString As String
	                  ToolTipString = InputBox("Enter the new ToolTip:", _
	                                    "Change ToolTip")
	                  If ToolTipString <> "" Then
	                     nid.szTip = ToolTipString & vbNullChar
	                     Shell_NotifyIcon NIM_MODIFY, nid
	                  End If
	               Case WM_RBUTTONUP
	               Case WM_RBUTTONDBLCLK
	            End Select
	        End Sub
	
	4. Press the F5 key to run the project or on the Tools menu, click Run Project.
	  Click Add Icon to add an icon to the taskbar status area. Double-click the
	  icon to change the icon. Right-click the icon to change the ToolTip string.
	  Click Delete Icon to remove the icon from the taskbar status area.
	
	REFERENCES
	==========
	
	"Hardcore Visual Basic," Bruce McKinney, Microsoft Press, 1995 Microsoft Win32
	SDK, Shell_NotifyIcon and NOTIFYICONDATA "Microsoft Systems Journal," February
	1996, "The Visual Programmer," page 93, Joshua Trupin "Visual Basic Programmer's
	Journal," March 1996, "Q & A," page 136, Carl Franklin
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbOSWin95 kbOSWin98 kbGrpDSVB kbDSupport kbOSWinME 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
