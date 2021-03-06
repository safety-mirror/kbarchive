---
layout: page
title: "Q139126: How To Connect to NetWare Resources through a RAS Connection"
permalink: /kb/139/Q139126/
---

## Q139126: How To Connect to NetWare Resources through a RAS Connection

{% raw %}

	Article: Q139126
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): WINDOWS:; winnt:3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	- Microsoft Windows for Workgroups 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	It is possible to access remote NetWare resources from a Windows for Workgroups
	3.11, Windows NT 3.5x, or Windows 95 Remote Access (RAS) client. This article
	discusses the requirements for accessing remote NetWare resources for each of
	these RAS clients. This article assumes the use of a Windows NT 3.5x Server as
	the RAS server.
	
	MORE INFORMATION
	================
	
	Windows for Workgroups 3.11 Client
	----------------------------------
	
	The Windows for Workgroups 3.11 RAS client only supports the NetBEUI protocol.
	Therefore, the RAS server must act as a gateway to the NetWare resources.
	
	On the RAS server, or any other Windows NT Server on the same network as your RAS
	server, you must perform the following steps:
	
	1. Install the NWLink IPX/SPX Compatible protocol.
	
	2. Install Gateway Services for NetWare (GSNW). GSNW is only available on
	  Windows NT Server.
	
	3. Use the GSNW icon in Control Panel to configure one or more Gateways to
	  NetWare resources on your LAN. By configuring a Gateway to these NetWare
	  resources, you are allowing access to NetWare resources from clients that are
	  unable to connect directly to your NetWare servers but are able to connect to
	  your Windows NT server.
	
	  On the Windows for Workgroups 3.11 RAS client, connect to the NetWare
	  resources by specifying the server name of the Windows NT Server running GSNW
	  and the share name defined for the NetWare resources. Choose the Windows NT
	  Server and share from the browse list or use the following format to connect
	  directly to the share using the Path field of File Manager's Connect Network
	  Drive dialog:
	
	  \\<Server_Name>\<Share_Name>
	
	Windows NT 3.5x RAS Client
	--------------------------
	
	Windows NT 3.5x RAS supports the IPX protocol over a RAS connection, eliminating
	the need to use a Gateway to access NetWare resources from the RAS client. The
	user account you use on your RAS client computer must have proper access
	permission to resources you connect to on the NetWare servers.
	
	On the RAS server, you must perform the following steps:
	
	1. Install the NWLink IPX/SPX Compatible protocol.
	
	2. Configure the RAS Server to allow remote clients running IPX. To enable this
	  option, use the Network Control Panel applet and configure the Remote Access
	  Service. Choose the Network button and select IPX in the Server Settings
	  section. NetBEUI and TCP/IP can be enabled or disabled.
	
	3. Choose the Configure button to the right of the IPX Checkbox. Make sure IPX
	  clients have access to the entire network by selecting the Entire Network
	  radio button.
	
	On the Windows NT RAS client, you must perform the following steps:
	
	1. Install the NWLink IPX/SPX Compatible protocol.
	
	2. Install Client Services for NetWare (CSNW).
	
	3. Edit your Remote Access PhoneBook entry for your RAS server and enable the
	  IPX protocol. To enable the IPX protocol, select the Network button and
	  select the IPX checkbox. You must use PPP as SLIP does not support the IPX
	  protocol.
	
	4. Once you are connected to the RAS server, connect to NetWare resources on the
	  remote network using File Manager or the NET USE command. If you connect
	  directly to the NetWare server instead of selecting the server and share from
	  the browse list, the server name you enter should be the server name of the
	  NetWare server and the share name should be the name of the volume on the
	  NetWare server.
	
	Windows 95 Dial-Up Networking Client
	------------------------------------
	
	Windows 95 Dial-Up Networking also supports IPX over the RAS connection. The user
	account you use on your Dial-Up Networking client computer must have proper
	access permission to resources you connect to on the NetWare servers.
	
	On the RAS server, you must perform the following steps:
	
	1. Install the NWLink IPX/SPX Compatible protocol.
	
	2. Configure the RAS Server to allow remote clients running IPX. To enable this
	  option, use the Network Control Panel applet and configure the Remote Access
	  Service. Choose the Network button and select IPX in the Server Settings
	  section. NetBEUI and TCP/IP can be enabled or disabled.
	
	3. Choose the Configure button to the right of the IPX Checkbox. Make sure IPX
	  clients have access to the entire network by selecting the Entire Network
	  radio button.
	
	On the Windows 95 Dial-Up Networking client, you must perform the following
	steps:
	
	1. Install the IPX/SPX Compatible protocol.
	
	2. Install the Microsoft Client for NetWare networks.
	
	3. Edit the properties of your Dial-Up Networking icon for your RAS server and
	  enable the IPX protocol. To enable the IPX protocol, choose the Server Type
	  button and enable the IPX/SPX Compatible checkbox in the Allowed Network
	  protocols section.
	
	4. Once you are connected to the RAS server, use the Network Neighborhood
	  application to connect to resources on remote NetWare servers.
	
	NOTE: If you use Windows NT RAS and you are running CSNW or Windows 95 Dial-Up
	Networking and you are running the Microsoft Client for NetWare networks and you
	connect with IPX to a remote, you will lose connectivity to all local NetWare
	servers. You will only have NetWare connectivity to the remote network. You
	cannot browse or reconnect to local NetWare servers as long as the RAS or
	Dial-Up Networking connection exists.
	
	For additional information on this limitation, please see the following articles
	in the Microsoft Knowledge Base:
	
	  Q128008 RAS: Connecting Using IPXCP Drops Local NetWare Session
	
	NetWare is manufactured by Novell, a vendor independent of Microsoft; we make no
	warranty, implied or otherwise, regarding this product's performance or
	reliability.
	
	Additional query words: Win95
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbAudDeveloper kbWFWSearch
	Version           : WINDOWS:; winnt:3.5,3.51
	
	=============================================================================
	

{% endraw %}
