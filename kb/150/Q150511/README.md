---
layout: page
title: "Q150511: Preventing SNA Server Keepalives on Idle LAN Connections"
permalink: /kb/150/Q150511/
---

## Q150511: Preventing SNA Server Keepalives on Idle LAN Connections

{% raw %}

	Article: Q150511
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	SNA Server Specific TCP/IP Keepalives
	-------------------------------------
	
	The WatchDogTimeOut parameter affects the TCP/IP timeout interval with all idle
	SNA client-server connections which are configured to use the TCP/IP sockets
	interface. These connections include sponsor, application, and Distributed Link
	Service (though not TN3270). The WatchDogTimeOut parameter can be configured for
	SNA Server, SNA distributed/remote link service, SnaBase, and for each SNA
	client platform (Windows NT, Windows 95, Windows 3.x).
	
	After the WatchDogTimeOut expires, the SNA Server client or server component
	sends an SNA Server specific TCP/IP message directed at the remote connection
	end pointBoth the Push and Acknowledgment bits are set, designated by
	A(cknowledgment)P(ush) bits. The following is an example SNA Server specific
	TCP/IP keepalive frame:
	
	  1605 24.920 SNA_CLIENT snaserver TCP .AP..., len:   36, seq:    224002,
	  ack: 463884666, win: 7476, src: 1026  dst: 1477  157.57.11.90 157.57.15.21
	  IP
	
	  Here is the data portion of the frame:
	                            24 00 00 06 CA FE 00 00 00 00   .4L...$.........
	  00040:  00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00   ................
	  00050:  00 00 00 00 00 00 1E 00 00 00                     ..........
	
	Bytes 5 and 6 (CA FE) designate an SNA Server specific keepalive.
	
	This frame is then repeated by the TCP/IP protocol at the following times in this
	example:
	
	26.781, 30.581, 38.182, 53.382, 83.802, 87.541 (time reflects seconds from
	beginning of capture). The delta in between each successive frame is
	approximately doubled.
	
	The SNA Server WatchdogTimeOut presently has an upper limit of 3600 seconds (1
	hour).
	
	TCP/IP Specific Keepalives
	--------------------------
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	TCP specific keepalives (initiated by TCP/IP itself; not initiated by a sockets
	application such as SNA Server) can be sent once every KeepAliveTime (defaults
	to 7,200,000 milliseconds or two hours), if 1) no data or 2) no SNA Server
	keepalives have been carried over the TCP connection.
	
	If there is no response to a TCP/IP specific keepalive, it is repeated once every
	KeepAliveInterval seconds. KeepAliveInterval defaults to 1 second. KeepAliveTime
	and KeepAliveInterval can be changed in the following subkey:
	
	Hkey_local_machine\system\CurrentControlSet\Services\Tcpip\Parameters
	
	The Problem with Keepalives in certain WAN Environments
	-------------------------------------------------------
	
	However, there are certain cases when either SNA Server specific or TCP/IP
	specific keepalives are not desired. One such case is when SNA Server
	connections are going over WAN links where link uptime is charged by unit of
	time, or by packet (ISDN links). In these environments, it is optimal to reduce
	the uptime or number of packets by reducing the overhead of keepalive packets
	when there is no information (user data) to be sent.
	
	RESOLUTION
	==========
	
	SNA Server Specific TCP/IP Keepalives
	-------------------------------------
	
	A fix was created to remove the one (two in SNA Server Service Pack 1) hour upper
	limit from the SNA Server WatchDogTimeOut registry/Win.ini parameter.
	
	TCP/IP Specific Keepalives:
	---------------------------
	
	A KeepAlive parameter was created to disable TCP/IPs own keepalives. By default,
	TCP/IP will send its own keepalives on an idle connection every 2 hours when an
	SNA Server connection is bound to TCP/IP. A fix was made to the Windows 3.x IP
	transport DLL (Ipcli.dll). The Windows NT and Windows 95 IP transport DLLs
	already support this parameter.
	
	The following registry entries/Win.ini entries are used to disable TCP/IP
	specific keepalives. The default is Yes.
	
	Windows NT
	----------
	
	HKLM\ 
	 System\ 
	   CurrentControlSet\ 
	     Services\ 
	       SnaBase\ 
	         Parameters\ 
	           SnaTcp\ 
	             KeepAlive:REG_SZ:YES | NO
	
	Windows 95
	----------
	
	HKLM\ 
	 Software\ 
	   Microsoft\ 
	     SnaBase\ 
	       Parameters\ 
	         SnaTcp\ 
	           KeepAlive:REG_SZ:YES | NO
	
	Windows 3.x
	-----------
	
	Win.ini file
	[WNAP]
	KeepAlive=YES | NO
	
	Configuring the SNA Server WatchDogTimeout Parameter
	----------------------------------------------------
	
	The SNA Server WatchDogTimeout parameter default to 60 seconds if not configured.
	Both the SNA client and the SNA Server send these SNA Server specific
	"keepalive" messages, so both ends must be adjusted to prevent timeouts over
	very slow connections.
	
	The following registry entires/WIN.INI entries are used to adjust these SNA
	Server specific keepalives.
	
	Windows NT
	----------
	
	HKLM\ 
	 System\ 
	   CurrentControlSet\ 
	     Services\ 
	       SnaBase\ 
	         Parameters\ 
	           WatchDogTimeOut: REG_DWORD: < decimal value, in seconds >
	
	Windows 95
	----------
	
	HKLM\ 
	 Software\ 
	   Microsoft\ 
	     SnaBase\ 
	       Parameters\ 
	         WatchDogTimeOut: REG_DWORD: <decimal value, in seconds>
	
	Windows 3.x
	-----------
	
	Win.ini file
	[WNAP]
	WatchDogTimeOut= <seconds >
	
	WARNING: Increasing the WatchDogTimeout above a few minutes on the server side
	may cause resource leakage if TCP/IP clients are not disconnected correctly.
	Disabling TCPs KeepAlive messages may also cause resource leakage, especially if
	the WatchDogTimeout is increased at the same time.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version
	2.11 and 2.11.sp1. This problem was corrected in the latest Microsoft SNA Server
	2.11 U.S. Service Pack. For information on obtaining the service pack, query on
	the following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
