---
layout: page
title: "Q163139: XADM: Err Msg 1005: Access Is Denied"
permalink: /kb/163/Q163139/
---

## Q163139: XADM: Err Msg 1005: Access Is Denied

{% raw %}

	Article: Q163139
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to install Microsoft Exchange Server version 4.0 to an NTFS
	partition, you may receive the following error message when the services attempt
	to start:
	
	  Error 0005 Access is denied.
	
	The corresponding Event Log error is as follows:
	
	  Event ID: 1005
	  Source:   MSExchangeSA
	  Type:     Error
	
	  Description:
	  The description for Event ID ( 1005) in Source ( MSExchangeSA ) could
	  not be found. It contains the following insertion string(s):
	  <<0xc0040000 - Network problems are preventing connection to the
	  Microsoft Exchange Server computer. Contact your system administrator if
	  this condition persists. MAPI was unable to load the information service
	  emsabp.dll. Be sure the service is correctly installed and configured.
	  Microsoft Exchange Address Book ID no: 00040380-0000-00000000>>.
	
	This is a result of insufficient Security permissions to the Exchsrvr directory
	structure. During Setup, the security privilege of Full Control is assigned to
	the group Everyone for the EXCHSRVR directory structure. The service account
	requires Full Control access to this directory structure.
	
	NOTE: These are the NTFS file/directory permissions, not the Share Level
	permissions.
	
	If the Everyone group permissions are changed on this directory structure, this
	may affect the ability of the Exchange Services to start properly.
	
	RESOLUTION
	==========
	
	To restore the Everyone group permissions, follow the procedure for your version
	of Windows NT Server, as shown below:
	
	For Windows NT Server 4.0:
	
	1. Start Windows NT Explorer.
	
	2. Right-click the Exchsrvr directory. Click Properties.
	
	3. On the Security tab, click the Permissions button.
	
	4. Select the group Everyone.
	
	5. In the list box, select Full Control.
	
	6. Select the Replace Permissions on Subdirectories check box and the Replace
	  Permissions on Existing Files check box.
	
	7. Click OK, and then click Yes.
	
	For Windows NT Server 3.51:
	
	1. Start File Manager.
	
	2. Select the Exchsrvr directory.
	
	3. Select Security, and then click Permissions.
	
	4. Select the group Everyone.
	
	5. In the list box, select Full Control.
	
	6. Select the Replace Permissions on Subdirectories check box and the Replace
	  Permissions on Existing Files check box.
	
	7. Click OK, and then click Yes.
	
	This will replace the default permissions for the Group Everyone in which the
	Service Account is a member.
	
	MORE INFORMATION
	================
	
	Here are some other errors that may result if the Service Account has
	insufficient NTFS permissions on the EXCHSRVR directory structure.
	
	- The Directory may fail with a 2140 resulting in an Event ID. -1032.
	
	- The Information Store may fail with a Server Specific error 4294965485,
	  resulting in an Event ID. -1811 or a Server Specific error 4294966264
	  resulting in an Event ID. -1032.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
