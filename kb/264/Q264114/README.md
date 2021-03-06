---
layout: page
title: "Q264114: PRB: VBCE -  Error Message &quot;INSTWZRD Encountered a Fatal Error&quot;"
permalink: /kb/264/Q264114/
---

## Q264114: PRB: VBCE -  Error Message &quot;INSTWZRD Encountered a Fatal Error&quot;

{% raw %}

	Article: Q264114
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbToolkit kbVBp600 kbOSWinCEsearch kbGrpDSVB kbDSupport
	Last Modified: 16-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0 
	- Microsoft eMbedded Visual Basic, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Application Install Wizard with the Windows CE Toolkit for
	Visual Basic (VBCE) immediately after selecting the location for the output
	files, the following error message may occur:
	
	  INSTWZRD Encountered a Fatal Error. This suggests that you have a bad or
	  corrupt install. Please reinstall "Windows CE Toolkit for Visual Basic 5.0".
	
	If you're using eMbedded Visual Basic (eVB), the following error may occur
	immediately after selecting the location for the output files:
	
	Unable to find list of available processors from the SDK specified by this
	project. Please verify that the most recent version of this platform SDK has
	been installed on your system.
	
	CAUSE
	=====
	
	The Application Install Wizard is attempting to read from the Vbce.ini file to
	populate the next screen in the wizard with target CPU choices. The Vbce.ini
	file may be missing or may contain invalid data.
	
	RESOLUTION
	==========
	
	The Vbce.ini file should contain the following sections:
	
	For the Handheld PC platform:
	
	[{0B7D1301-289F-11D2-974F-00A0240918F0}]
	SH 3 (1K) v2.0=4,3,2,0,1024,10003
	Mips 3000 (4K) v2.0=1,3,2,0,4096,4000
	Mips 4000 (1K) v2.0=1,4,2,0,1024,4000
	
	For the Handheld PC Pro platform:
	
	[{74239C21-1DCA-11D2-9747-00A0240918F0}]
	SH 3 (1K) v2.10=4,3,2,10,1024,10003
	SH 4 (4K) v2.10=4,4,2,10,4096,10005
	Mips 4000 (1K) v2.10=1,4,2,10,4096,4000
	Arm 1100 (4K) v2.10=5,4,2,10,4096,2577
	
	For the Handheld PC 2000 platform:
	
	[{0F9D255B-97DA-4641-A8E6-7A7411D2472F}]
	Mips 3000 (4K) v3.00=1,3,3,0,4096,4000
	Mips 4000 (4K) v3.00=1,4,3,0,4096,4000
	I486 (4K) v3.00=0,0,3,0,4096,486
	Arm 1100 (4K) v3.00=5,4,3,0,4096,2577
	
	For the Palm-size PC platform:
	
	[{458BFDB0-A6A6-11D2-BBCF-00A0C9C9CCEE}]
	SH 3 (1K) v2.11=4,3,2,10,1024,10003
	Mips 3000 (4K) v2.11=1,3,2,10,4096,4000
	Mips 4000 (1K) v2.11=1,4,2,10,1024,4000
	
	<B>For the PocketPC 2000 platform</B>: 
	[{6D5C6210-E14B-11D2-B72A-0000F8026CEE}]
	SH 3 (1K) v3.00=4,3,3,0,1024,10003
	Mips 4000 (4K) v3.00=1,4,3,0,4096,4000
	Arm 720T (4K) v3.00=5,4,3,0,4096,1824
	Arm 1100 (4K) v3.00=5,4,3,0,4096,2577
	
	For the PocketPC 2002 platform:
	
	[{DE9660AC-85D3-4C63-A6AF-46A3B3B83737}]
	Arm 1100 (4K) v3.00=5,4,3,0,4096,2577
	I486 (4K) v3.00=0,0,3,0,4096,486
	
	If any of the preceding sections are missing, paste the text into the Vbce.ini
	file for the targeted platform and try running the Application Install Wizard
	again.
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: vbce vbce6 wce evb instwzrd
	
	======================================================================
	Keywords          : kbToolkit kbVBp600 kbOSWinCEsearch kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword2 kbVBeMbSearch kbWinCETKVBSearch kbWinCESearch kbVBeMb300
	Version           : :3.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
