---
layout: page
title: "Q58327: Windows 3.0 WIN.INI &#91;windows&#93; Section"
permalink: /kb/058/Q58327/
---

## Q58327: Windows 3.0 WIN.INI &#91;windows&#93; Section

{% raw %}

	Article: Q58327
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information is contained in the Microsoft Windows 3.0 WININI.TXT
	online document. The Windows Setup program copies this text file to your Windows
	directory.
	
	MORE INFORMATION
	================
	
	[WINDOWS] SECTION
	-----------------
	
	The [windows] section contains settings that affect the following
	parts of your Windows environment:
	
	* Applications that start with Windows
	* File extensions
	* Keyboard output
	* Mouse output
	* Null communication port
	* Printed output
	* Warning beep
	* Window border width
	
	The [windows] section can contain the following settings:
	
	----------------------------------------------------------------------
	Beep=<yes-or-no>
	Default:   Yes
	Purpose:   If this setting is enabled, Windows sounds a warning beep
	          when you attempt to do something that is not allowed.
	To change: Choose the Sound icon from the Control Panel window.
	----------------------------------------------------------------------
	BorderWidth=<integer>
	Default:   3
	Purpose:   Sets the width of the borders around all the windows on
	          your desktop except those (such as Control Panel) that are
	          fixed. The allowed range is 1 (narrowest) to 49 (widest).
	To change: Choose the Desktop icon from the Control Panel window.
	----------------------------------------------------------------------
	CursorBlinkRate=<milliseconds>
	Default:   530
	Purpose:   Indicates how many milliseconds elapse between each time
	          the cursor blinks (flashes off and on).
	To change: Choose the Desktop icon from the Control Panel window.
	----------------------------------------------------------------------
	Device=<output-device-name, device-driver, port-connection>
	Default:   None
	Purpose:   Defines the default printer. The <output-device-name>
	          value can be any device name given in the [devices]
	          section. An explicit port and driver must be assigned to
	          the device. The <device-driver> value is the filename
	          (without the extension) of the device-driver file. The
	          <port-connection> value is any port name given in the
	          [ports] section.
	To change: Choose the Printers icon from the Control Panel window.
	----------------------------------------------------------------------
	DeviceNotSelectedTimeout=<seconds>
	Default:   15
	Purpose:   Tells Print Manager the number of seconds to wait for a
	          device to be switched on. If the device is not switched on
	          during this time, Print Manager won't print to the device.
	          Note that for some devices, Print Manager immediately posts
	          an error message if the device is not already switched on.
	To change: Choose the Printers icon from the Control Panel window.
	----------------------------------------------------------------------
	Documents=<extensions>
	Default:   None
	Purpose:   Defines which files Windows identifies as documents.
	          Separate each extension name with a space, and do not
	          include periods (for example, TXT).
	To change: Use Notepad to edit the WIN.INI file.
	----------------------------------------------------------------------
	DoubleClickSpeed=<milliseconds>
	Default:   452
	Purpose:   Establishes the maximum amount of time between clicks of
	          the mouse button that the system will permit for one
	          double-click. The lower the value, the less time the user
	          has to click twice in order to effect a double-click.
	To change: Choose the Mouse icon from the Control Panel window.
	----------------------------------------------------------------------
	KeyboardSpeed=<milliseconds>
	Default:   31
	Purpose:   Establishes how much time elapses between repetitions of a
	          character on the display when you hold down a keyboard key.
	To change: Choose the Keyboard icon from the Control Panel window.
	----------------------------------------------------------------------
	Load=<filename(s)>
	Default:   None
	Purpose:   Tells Windows to load a particular application and run it
	          as an icon when Windows is started. This value is a list of
	          one or more application filenames, separated by commas or
	          spaces.
	To change: Use Notepad to edit the WIN.INI file.
	----------------------------------------------------------------------
	MouseSpeed=<speed-option>
	Default:   1
	Purpose:   Establishes the relationship between mouse movement and
	          cursor movement when either the value of MouseThreshold1 or
	          MouseThreshold2 is exceeded. When this occurs, Windows
	          causes cursor movement to accelerate according to the
	          <speed-option> value. If it is 0, there is no acceleration.
	          If it is 1, the cursor is moved twice the normal speed when
	          mouse movement exceeds the value of MouseThreshold1. If it
	          is 2, the cursor is moved twice the normal speed when mouse
	          movement exceeds the value of MouseThreshold1 or four times
	          the normal speed if mouse movement exceeds MouseThreshold2.
	To change: Choose the Mouse icon from the Control Panel window.
	----------------------------------------------------------------------
	MouseThreshold1=<pixels>
	Default:   5
	Purpose:   Establishes the maximum number of pixels that the mouse can
	          move between mouse interrupts before Windows alters the
	          relationship between mouse movement and cursor movement. If
	          the mouse movement exceeds this threshold and MouseSpeed is
	          greater than zero, Windows causes the cursor to move at
	          twice the normal speed.
	To change: Choose the Mouse icon from the Control Panel window.
	----------------------------------------------------------------------
	MouseThreshold2=<pixels>
	Default:   10
	Purpose:   Establishes the maximum number of pixels that the mouse can
	          move between mouse interrupts before Windows alters the
	          relationship between mouse movement and cursor movement. If
	          the mouse movement exceeds this threshold and MouseSpeed is
	          equal to 2, Windows causes the cursor to move at four times
	          the normal speed.
	To change: Choose the Mouse icon from the Control Panel window.
	----------------------------------------------------------------------
	NullPort=<null-portname>
	Default:   None
	Purpose:   Specifies the name used for a null port. This name is used
	          in cases where a device is installed (that is, the device
	          driver is present) but is not connected to any port.
	To change: Use Notepad to edit the WIN.INI file.
	----------------------------------------------------------------------
	Programs=<extensions>
	Default:   COM EXE BAT PIF
	Purpose:   Defines which files Windows regards as applications.
	          Extension names are separated by a space and do not include
	          periods.
	To change: Use Notepad to edit the WIN.INI file.
	----------------------------------------------------------------------
	Run=<filename(s)>
	Default:   None
	Purpose:   Tells Windows to load one or more specified applications
	          and run them in windows when Windows is started. The value
	          is a list of one or more application filenames, separated
	          by commas or spaces.
	To change: Use Notepad to edit the WIN.INI file.
	----------------------------------------------------------------------
	Spooler=<yes-or-no>
	Default:   Yes
	Purpose:   Specifies whether output to the printer is to be sent
	          through Print Manager. The default value is "yes". Setting
	          this value to "no" disables Print Manager.
	To change: Choose the Printers icon from the Control Panel window.
	----------------------------------------------------------------------
	TransmissionRetryTimeout=<seconds>
	Default:   45
	Purpose:   Tells Print Manager the amount of time allowed for
	          attempted transmission retries. If a successful
	          transmission does not occur during this time, Print Manager
	          posts a message box stating that the printer is not
	          receiving characters.
	To change: Choose the Printers icon from the Control Panel window.
	
	Additional query words: 3.00 3.0 3.0a 3.00a win30
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a
	Version           : WINDOWS:3.0,3.0a
	
	=============================================================================
	

{% endraw %}
