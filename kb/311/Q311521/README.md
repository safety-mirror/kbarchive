---
layout: page
title: "Q311521: HOW TO: Index ASP.NET Content by Using MS Index Server"
permalink: /kb/311/Q311521/
---

## Q311521: HOW TO: Index ASP.NET Content by Using MS Index Server

{% raw %}

	Article: Q311521
	Product(s): Internet Information Server
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbreadme kbDSupport kbHOWTOmaster
	Last Modified: 14-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Index Server version 3.0 
	- Microsoft.NET Framework 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Use Registry Editor to Index ASP.NET Content Types
	- More Information
	
	SUMMARY
	=======
	
	On a Microsoft Windows 2000-based system (earlier than Service Pack 3),
	Microsoft Index Server does not, by default, index ASP.NET content types, such
	as .aspx and .ascx files.
	
	If you (as an administrator) want to enable indexing of ASP.NET content types,
	use the contents of the registry file included in the following section of this
	article. This file associates .aspx files and .ascx files with the Index Server
	HTML filter, and therefore ensures that the content is filtered correctly and
	the visual content is displayed without revealing source code.
	
	Use Registry Editor to Index ASP.NET Content Types
	--------------------------------------------------
	
	To use Registry Editor to associate .aspx files and .ascx files with the Index
	Server HTML filter, follow these steps.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. Paste the following text into a text document:
	
	  REGEDIT4
	
	  [HKEY_CLASSES_ROOT\.aspx\PersistentHandler]
	  @="{eec97550-47a9-11cf-b952-00aa0051fe20}"
	
	  [HKEY_CLASSES_ROOT\.ascx\PersistentHandler]
	  @="{eec97550-47a9-11cf-b952-00aa0051fe20}"
	
	2. Rename the file with a .reg extension, and then execute the newly created
	  .reg file.
	
	3. Restart the server.
	
	4. Stop the Index Server service.
	
	5. Delete the contents of the Catalog.wci folder associated with the catalog
	  that you are working on.
	
	6. Restart the Index Server service, and then allow the catalog to fully
	  rebuild.
	
	More Information
	----------------
	
	Index Server can be configured to index unknown content types, in which case,
	ASP.NET content will be indexed by default, with or without the registry
	entries. If the entries are present, the correct filtering will be performed for
	.aspx and .ascx files. Otherwise, these files will be treated as text, which is
	generally not optimal for a site that is set up to perform indexing. Note that
	regardless of the registry settings, other ASP.NET content types (for example,
	.asmx files and .config files) are not handled by the HTML filter. If a Web site
	is configured to index these content types, you should exercise care to limit
	search queries so that they do not contain these types and inadvertently expose
	application data or source material.
	
	Note that Windows 2000 Service Pack 3, Microsoft Windows XP, and Microsoft
	Windows .NET Server contain the registry entries that associate .aspx and .ascx
	to the Index Server HTML filter by default.
	
	Additional query words: kbreadme
	
	======================================================================
	Keywords          : kbreadme kbDSupport kbHOWTOmaster 
	Technology        : kbIdxServSearch kbAudDeveloper kbNETFrame
	Version           : :3.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
