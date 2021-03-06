---
layout: page
title: "Q327235: Host Account Cache Does Not Start and Posts Events 5, 1281 and 7"
permalink: /kb/327/Q327235/
---

## Q327235: Host Account Cache Does Not Start and Posts Events 5, 1281 and 7

{% raw %}

	Article: Q327235
	Product(s): Microsoft SNA Server
	Version(s): 
	Operating System(s): 
	Keyword(s): Kbhostintegserv2000
	Last Modified: 13-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The SNA Host Account Cache (HAC) service may not start after the initial install
	of Host Security Integration components that are available in Host Integration
	Server 2000. For additional information about Host Security Integration, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q175063 Host Security Integration Setup and Architectural Overview
	
	The following events may be posted in the application log of the Event Viewer:
	
	  Event Source: SNA Host Security
	  Event ID: 5
	  Description: Unable to create a new key container: UdbKeyContainer. Error:
	  Keyset does not exist.
	
	  Event Source: SNA Host Security
	  Event ID: 1281
	  Description: Unable to initialize the database Supplied code %1
	
	The following events may be posted in the system log of the Event Viewer:
	
	  Event Source: Service Control Manager
	  Event ID: 7024
	  Description: The SNA Host Account Cache service terminated with
	  service-specific error 3781166337
	
	CAUSE
	=====
	
	The following lists some possible causes for the "Symptoms" described earlier:
	
	- The Crypto subsystem has become corrupted.
	
	- The UDB key does not exist, for one of the following possible reasons:
	
	   - An error occurred during the setup process.
	
	   - The UDB key was deleted by an Administrator.
	
	- A policy restricted account or a corrupted user account was specified for SNA
	  services or Host Security services during installation of Host Integration
	  Server 2000.
	
	RESOLUTION
	==========
	
	IMPORTANT: This article contains information about modifying the registry.
	Before you modify the registry, make sure to back it up and make sure that you
	understand how to restore the registry if a problem occurs. For information
	about how to back up, restore, and edit the registry, click the following
	article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve the issue if you suspect that the Crypto subsystem is corrupted,
	follow these steps:
	
	1. Click Start, click Run, and then type "regedit" (without the quotation marks)
	  to start Registry Editor.
	
	2. Locate the following registry key:
	
	  HKEY_USERS\Default\Software\Microsoft\Cryptography\Providers\Type 001
	
	3. Click the Providers registry key, on the Registry menu, click Export Registry
	  File, and then select a location in which to save this file for backup
	  purposes.
	
	4. After you have exported the registry key, delete the Type 001 registry key.
	
	5. Quit Registry Editor.
	
	6. Restart the server.
	
	For additional information about how to resolve the issue if you suspect that the
	UDB key is corrupted, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q276681 HAC Does Not Start If Database Key Does Not Exist
	
	If you suspect that the user account has become corrupted, remove the Host
	Security Integration components, and then reinstall the program. During
	reinstallation, specify a user account that does not exist so that the Host
	Integration Server 2000 Setup routine creates the account and automatically
	grants the correct privileges and membership. For additional information about
	permissions and membership granted, click the article number below to view the
	article in the Microsoft Knowledge Base:
	
	  Q193832 Permissions Needed on SNA Server Services User Account
	
	MORE INFORMATION
	================
	
	When this problem occurs, SNA Host Account Cache Internal traces (Udbintx.atf)
	typically show the following statements:
	
	0e8c:0b7c 13:00:08.0572 udbsvce.cpp(126)   main Trace Initialization succeeded
	0e8c:0e34 13:00:08.0572 udbsvce.cpp(875)   Udb_Service_Status Set service Status to 2, CheckPoint: 1, Service exit code: 0
	0e8c:0e34 13:00:08.0572 udbsvce.cpp(545)   InitResources Got the service main thread handler
	0e8c:0e34 13:00:08.0588 udbsvce.cpp(579)   InitResources Got server name of this computer: A01DC004
	0e8c:0e34 13:00:08.0588 udbsvce.cpp(608)   InitResources Registry initialization succeeded
	0e8c:0e34 13:00:08.0588 hscrypto.cpp(900)  LazyProcessInit Redefiniation of directed security functions succeeded
	0e8c:0e34 13:00:08.0588 hscrypto.cpp(354)  SetKeyContext Failed to acquire key container. Message: Keyset does not exist
	                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
	0e8c:0e34 13:00:08.0588 hscrypto.cpp(393)  SetKeyContext Unable to create the new key container, Error: Keyset does not exist
	                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
	0e8c:0e34 13:00:08.0588 udbcrypto.cpp(84)  Init CHsCrypto Constructor failed !
	                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
	0e8c:0e34 13:00:08.0588 udbsvce.cpp(619)   InitResources Crypto object initialization failed
	                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
	0e8c:0e34 13:00:08.0588 udbsvce.cpp(228)   Udb_Start Resource Initialization failure, exit
	                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
	0e8c:0b7c 13:00:08.0588 udbsvce.cpp(137)   main Start service control returned
	0e8c:0b7c 13:00:08.0588 udbsvce.cpp(143)   main Wait for Service main thread
	0e8c:0e34 13:00:08.0588 udbsvce.cpp(875)   Udb_Service_Status Set service Status to 1, CheckPoint: 0, Service exit code: 3781166337
	
	Additional query words:
	
	======================================================================
	Keywords          : Kbhostintegserv2000 
	Technology        : kbAudDeveloper kbHostIntegServ2000
	Version           : :
	Issue type        : kbinfo kbhostintegserv2000
	
	=============================================================================
	

{% endraw %}
