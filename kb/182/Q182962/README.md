---
layout: page
title: "Q182962: XADM: Pfadmin: Setacl Sets &quot;Default&quot; User Role to None"
permalink: /kb/182/Q182962/
---

## Q182962: XADM: Pfadmin: Setacl Sets &quot;Default&quot; User Role to None

{% raw %}

	Article: Q182962
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 27-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The default user role, which by default is set to "Author" on every public
	folder, when touched by the PFAdmin (setacl) command or processes is changed to
	"none". In other words, there is a default role of permissions for every public
	folder and the default is Author. PFAdmin setacl run against any folder changes
	the default role to "none" regardless of what the user intended.
	
	RESOLUTION
	==========
	
	This problem has been fixed in PFAdmin utility that ships on the Exchange 5.5
	CD-ROM in the support\autorun\reskit subdirectory and will also be available
	with BackOffice Resource Kit Part III. PFAdmin version is 1.2.1 or later.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the BackOffice Resource Kit
	(BORK) Parts I and II. The problem has been fixed in the BORK Part III.
	
	MORE INFORMATION
	================
	
	This problem can be identified by going to the Public Folder Properties page and
	using the Client Permissions button on the General tab.
	
	The default user role is not modifiable within earlier versions of the PFAdmin
	tool. Modification of the default user role requires manually changing each
	public folder's client permissions, regardless of what the Microsoft BackOffice
	Resource Kit documentation states (see the following):
	
	Help on PFADMIN SETACL Utility
	------------------------------
	
	The following are examples of typical syntax usage for the PFAdmin tools:
	
	  pfadmin <profile> setacl all "pf global admin" owner "pf lead" o
	  pfadmin <profile> setacl "Readme FAQ\Exchange Discussion"UserNamer
	  pfadmin <profile> setacl all default read
	
	All entries are case-insensitive. You must use quotation marks when typing names
	containing blanks and use backslashes when typing subfolder names, starting with
	the top-level folder under All Public Folders.
	
	You can specify user rights by typing either a full name or character(s). You can
	combine rights by using the '|' symbol [for example, read | write (blanks
	optional)] or joining characters into a single word (for example, RW).
	
	You can use the following command-line syntax format when running PFAdmin:
	
	PFADMIN [Switches] Profile SETACL Folder|ALL User Rights [User Rights]...
	[YES|NO]
	
	Following is a list of the command-line switches available in PFAdmin:
	
	  /En = eventlog logging level (default = 3)
	  /Cn = console logging level (default = 4)
	  /Dn = debug file logging level (default = 5)
	  /Ln = logging level (console, debug, and EventLog)
	
	where 0=NONE, 1=STATUS, 2=ERROR, 3=WARNING, 4=INFO, 5=DEBUG
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
