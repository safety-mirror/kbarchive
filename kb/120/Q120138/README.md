---
layout: page
title: "Q120138: Errors Creating Files or Folders in the Root Directory"
permalink: /kb/120/Q120138/
---

## Q120138: Errors Creating Files or Folders in the Root Directory

{% raw %}

	Article: Q120138
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): diskmem win95 kbDiskMemory
	Last Modified: 04-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 98 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	You may receive an error message when you create a file or folder in the root
	directory. The exact error message depends on the method used to create the file
	or folder.
	
	Using the COPY command in an MS-DOS session reports the following:
	
	  Cannot make directory entry - <filename>
	
	WordPad and Paint report the following when saving a file to the root directory:
	
	  <filename>: This filename is not valid.
	
	When you try to create a new folder in the root directory in My Computer or
	Windows Explorer, you receive the following error message:
	
	  Unable to create <"New Folder">. Make sure the disk is not full or
	  read-only.
	
	NOTE: This information is accurate for a standard file allocation table 16
	(FAT16) file system, but does not apply to a FAT32 file system. For more
	information about FAT32, see the following article in the Microsoft Knowledge
	Base:
	
	  Q154997 Description of the FAT32 File System
	
	CAUSE
	=====
	
	This problem occurs when all 512 root directory entries have been used. This
	problem can also occur with fewer than 512 files and folders in the root
	directory because Windows 95 uses additional directory entries to store long
	file names.
	
	STATUS
	======
	
	To ensure compatibility with MS-DOS, Windows 95 uses a standard file allocation
	table (FAT) file system. The root directory for a FAT drive has a fixed size and
	is stored in a fixed location on the disk. All hard disk drives use 32 sectors
	of 512 bytes each to store the root directory. This limits the root directory on
	a hard disk drive to 16K: 32 sectors x 512 bytes per sector = 16,384 bytes, or
	16K.
	
	MS-DOS uses one directory entry for each file and folder, but Windows 95 uses
	additional directory entries to store long file names and folder names, and the
	associated 8.3 aliases. This means that you can run out of directory entries
	with fewer than 512 files or folders in the root directory.
	
	Folders do not have a fixed size, so the only limitation to the number of files
	or folders you can store in any folder with Windows 95 is free disk space. For
	this reason, it is best to store your files (programs and data) in a folder off
	the root directory.
	
	RESOLUTION
	==========
	
	Use the following steps to free root directory entries:
	
	1. Check the drive for invalid long file names, and then defragment the drive as
	  follows:
	
	  Use the right mouse button to click the drive icon in My Computer or Windows
	  Explorer and the click Properties on the menu that appears. Click the Tools
	  tab and then click Check Now. Perform the default correction if invalid long
	  file names are found. Then choose Defragment Now.
	
	2. Rename any files or folders in the root directory using only upper- case
	  8.3-compliant file or folder names.
	
	  The characters that are valid for an 8.3-compliant file or folder name include
	  any combination of letters (A-Z) and/or numbers (0-9), plus the following
	  special characters:
	
	     $   Dollar sign
	     %   Percent sign
	     '   Apostrophe
	     `   Opening single quotation mark
	     -   Hyphen
	     @   At sign
	     {   Left brace
	     }   Right brace
	     ~   Tilde
	     !   Exclamation point
	     #   Number sign
	     (   Opening parenthesis
	     )   Closing parenthesis
	     &   Ampersand
	     _   Underscore
	     ^   Caret
	
	3. Move some files or folders out of the root directory.
	
	MORE INFORMATION
	================
	
	An MS-DOS FAT root directory contains a separate entry for every file and folder
	it contains. These directory entries contain information such as the file name,
	extension, attributes, time and date the file was last modified, the starting
	cluster number, and the file size. Each directory entry uses 32 bytes to store
	this information. Because the root directory is 16K in size, it can contain a
	maximum of 512 directory entries, which are 32 bytes each.
	
	When you name a file or folder in Windows, the system creates a primary file
	name, which can be a long file name, and an MS-DOS-compliant 8.3 alias. If the
	file or folder name is already 8.3-compliant, only one directory entry is used.
	
	NOTE: For a file or folder name to be 8.3-compliant, it must contain only those
	characters that are valid for an 8.3 alias name, and it must be composed of all
	uppercase characters.
	
	Windows 95/98 allows file and folder names to contain up to 250 characters. Valid
	characters for a Windows 95 file name include all the valid MS-DOS file name
	characters, the space character, and the following additional characters:
	
	  +   Plus sign
	  ,   Comma
	  .   Period
	  =   Equal sign
	  [   Opening bracket
	  ]   Closing bracket
	
	Windows 95 file names are not case sensitive, but the case is preserved. The
	primary file names can include upper, lower, or mixed-case characters. For
	example, you can name a file "MyText.txt" and the file system preserves the case
	formatting.
	
	If the file name is not 8.3-compliant, Windows 95 automatically generates an 8.3
	alias for the file name. An additional directory entry is used to store the 8.3
	alias. If the primary file name contains more than 13 characters, an additional
	directory entry is used.
	
	The following table shows some primary file names, their 8.3 aliases, and
	directory entry usage in Windows 95:
	
	  Primary               Possible       Directory
	  file name             8.3 alias      entries used
	  -------------------------------------------------
	  EXAMPLE.TXT           EXAMP~1.TXT         1
	  Example.txt           EXAMP~1.TXT         2
	  !@#$%&().{^}          !@#$%&~1.{^}        1
	  !@#$%&().{+}          !@#$%&~1.{}         2
	  LFN TEST.TXT          LFNTES~1.TXT        2
	  This is a LFN.TEST    THISIS~1.TES        3
	  This is a very long
	   file name.test       THISIS~2.TES        4
	
	NOTE: Any file whose name contains more than 13 characters requires 3 or more
	directory entries.
	
	
	Additional query words: lfns ldns vfat VM wwt fat root limit
	
	======================================================================
	Keywords          : diskmem win95 kbDiskMemory 
	Technology        : kbWin95search kbWin98search kbZNotKeyword3 kbWin98
	Version           : :
	
	=============================================================================
	

{% endraw %}
