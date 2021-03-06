---
layout: page
title: "Q142558: Adding Mime Types to Internet Information Server"
permalink: /kb/142/Q142558/
---

## Q142558: Adding Mime Types to Internet Information Server

{% raw %}

	Article: Q142558
	Product(s): Internet Information Server
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 28-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Mime types allow files to be opened by "helper" applications on web browser
	clients, such as Microsoft Internet Explorer. Currently, mime types for Internet
	Information Server (IIS) must be added manually to the registry. There is no
	graphical interface for adding mime types at this time.
	
	MORE INFORMATION
	================
	
	IIS installs the most common mime types by default. Mime types for new
	applications or applications that are not widely used will have to be added
	manually. Note that a helper application may have to be configured on the client
	as well. Mime entries can be added to the following registry location:
	
	HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InetInfo\Parameters\
	MimeMap
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	To add an entry, open the MimeMap key and choose Edit Value or Add Value.
	
	The mime information needs to be placed in the Value Name box. The data type for
	the entry should be set to REG_SZ, the string field should be left blank. The
	following is an example of a mime entry:
	
	  image/gif,gif,,5:REG_SZ:
	
	  <mime/type>,<extension>,<unused>,<gopher item type>
	
	The unused field is represented by an extra comma between 'gif' and '5'. The
	extra comma must be included for the mime type to work correctly.
	
	NOTE: Only the gopher server uses the Gopher item type. The gopher item types are
	listed below. In the above example, the gopher item type '5' describes the file
	type as an MS-DOS binary archive.
	
	Gopher Item Types
	-----------------
	
	The following list shows all possible Gopher item type codes and what they mean.
	The first character is the type code.
	
	  0 A file, usually a flat text file
	  1 A Gopher directory
	  2 A CSO phone-book server
	  3 An error
	  4 A BinHex'ed Macintosh(r) file
	  5 An MS-DOS binary archive
	  6 A UNIX Uuencoded file
	  7 An index-search server
	  8 A Telnet session
	  9 A binary file
	  c A calendar or calendar of events
	  g A graphic interchange file (GIF) graphic
	  h An HTML World Wide Web hypertext page
	  i An in-line text that is not an item
	  I Another kind of image file
	  m A BSD format mbox file
	  P A PDF document
	  T A TN3270 mainframe session
	  : A bitmap Image (use Gopher Plus information for type of image)
	
	Additional query words: prodiis1
	======================================================================
	Keywords          : kbusage 
	Technology        : kbiisSearch kbiis100
	Version           : 1.0
	
	=============================================================================
	

{% endraw %}
