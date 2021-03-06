---
layout: page
title: "Q113503: Overview of Disk Volume Sets in Windows NT"
permalink: /kb/113/Q113503/
---

## Q113503: Overview of Disk Volume Sets in Windows NT

{% raw %}

	Article: Q113503
	Product(s): Microsoft Windows NT
	Version(s): ; winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbother
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Volume sets more effectively use memory under Windows by combining free disk
	space on from one to 32 disks into a single volume with a single drive letter.
	
	MORE INFORMATION
	================
	
	Here are the important facts about volume sets in Windows NT:
	
	Characteristics
	---------------
	
	- Both Windows NT Server and Windows NT Workstation can create and use volume
	  sets.
	
	- Volume sets provide no fault tolerance; if even one area of disk space in the
	  set is lost, all the data is lost.
	
	- Volume sets are transparent to the user. When a volume set is created all
	  areas of free space are assigned the same drive letter.
	
	- Volume sets are the only Windows NT disk partition management option that
	  allows more than one area of disk space in the set to reside on the same
	  physical hard disk.
	
	- Volume sets are the only Windows NT disk partition management option that
	  allows the individual areas of disk space making up the volume to be of
	  different sizes.
	
	Creating Volume Sets
	--------------------
	
	- Volume sets must be created from free disk space--they cannot be used with
	  existing partitions.
	
	- To create a volume set, first select free space on 1 to 32 disks, then select
	  Create Volume Set from the Partition menu in Disk Administrator.
	
	- Shut down and restart the computer. When Windows NT restarts, Autochk.exe
	  will run the equivalent of "chkdsk /f" on the entire volume set and the
	  volume set will be created or extended. You can then format it for a file
	  system.
	
	  NOTE: The chkdsk procedure must complete before the volume set will be
	  accessible and may take many hours depending on the volume size and directory
	  and file structure. For additional information, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q187941 An Explanation of the New CHKDSK /C and /I Switches
	
	- Volume sets are file system independent and can be formatted with any hard
	  disk file system installed with Windows NT.
	
	- Volume sets can be created on 1 disk or as many as 32.
	
	Configuration Characteristics
	-----------------------------
	
	- Normally, only the Windows NT installation that created the volume set will
	  recognize it--other operating systems will not. MS-DOS will identify the
	  different areas of disk space in the volume set as "Non- DOS." From within
	  other Windows NT installations, Disk Administrator will identify the areas of
	  disk space in the volume set as having an "Unknown" file system.
	
	- Other installations of Windows NT on the same computer can recognize a volume
	  set created by a different installation of Windows NT by restoring disk
	  configuration information. See page 529 of the "Windows NT Advanced Server
	  System Guide" for more information.
	
	- You cannot install Windows NT on an existing volume set. Setup describes
	  volume set partitions as "Windows NT Fault Tolerance." If you attempt to
	  select one of these partitions for installation, a message states that
	  Windows NT does not recognize this partition, and you must delete it before
	  Setup can use it.
	
	- Volume sets may offer somewhat better performance than input and output from
	  a single partition, but their main advantage is that they allow the most
	  efficient use of hard disk space.
	
	REFERENCES
	==========
	
	Windows NT Advanced Server System Guide, page 529.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbother 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : :; winnt:3.5,3.51,4.0
	
	=============================================================================
	

{% endraw %}
