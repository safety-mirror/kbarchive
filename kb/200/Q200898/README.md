---
layout: page
title: "Q200898: SMS: How to Use Systems Management Server Through a Firewall"
permalink: /kb/200/Q200898/
---

## Q200898: SMS: How to Use Systems Management Server Through a Firewall

{% raw %}

	Article: Q200898
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbsetup kbConfig kbsms200 smssetup smsconfig smssenders kbSMSSender
	Last Modified: 04-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	One way of using Systems Management Server through a firewall is to configure
	the firewalling or proxy server to allow standard and (MS) RPC port traffic to
	pass.
	
	MORE INFORMATION
	================
	
	Systems Management Server UDP Information
	-----------------------------------------
	
	When NetBIOS over TCP/IP is selected for Systems Management Server Remote
	Control, the system uses the following ports:
	
	  Port 137 - name resolution
	  Port 138 - messaging (sending the screen image)
	  Port 139 - client sessions
	
	When NetBIOS over NWLink is used, the router must forward Type 20 packets (the
	packets that provide NetBIOS support).
	
	Microsoft Windows NT UDP Information
	------------------------------------
	
	The following list contains the core UDP ports that Windows NT uses and their
	function:
	
	  DNS                 udp         53
	  DHCP                udp         67
	  RPC                 TCP        135
	  WINS                udp        137
	  NetBIOS datagrams   udp        138
	  NetBIOS datagrams   tcp        139
	
	NetBIOS sessions  TCP  139
	--------------------------
	
	To list established connections, type "netstat -a" (without the quotation marks)
	from a command prompt. This returns additional UDP ports that a computer running
	Windows NT Server or Windows NT Workstation is using beyond the core, due to
	additional services or applications installed on the Windows NT system.
	
	Microsoft SQL Server UDP Information
	------------------------------------
	
	If you are using TCP/IP Net-Library, enable port 1433 on the firewall. Use the
	HOSTS file or an advanced connection string for host name resolution.
	
	If you are using Named Pipes over TCP/IP, enable port 139 for NetBIOS functions.
	UDP ports 137 and 138 can be enabled for NetBIOS name resolution using b-node
	broadcast, but this is not recommended. Instead, a WINS server or LMHOSTS file
	should be used.
	
	When SQL Server 6.x is configured to listen on TCP/IP, it uses TCP (not UDP) port
	1433 by default. This port can be configured by running SQL Server Setup on the
	server and clicking the Change Network Support option. If the default port 1433
	is used, the client Net-Library works by default. If a custom port number is
	used, the client needs to specify that port in the DSN.
	
	Security Notes
	--------------
	
	For added security, using IP filters with your firewall server can be configured
	to allow only "registered" addresses use of the ports. There are certain
	security concerns created by enabling specific ports on a proxying or
	firewalling server. For additional information about these concerns, visit
	http://www.microsoft.com/security.
	
	Another method of providing Systems Management Server site, client, and
	administrative communication through a firewall could be to use the Systems
	Management Server RAS Sender with a Point to Point Tunneling Protocol (PPTP; TCP
	port 1723) client and server to configure which port is used for initializing
	the session, then allow that specific port to be open on the firewall server.
	
	Remote Tools:
	-------------
	
	For additional information about remote tools, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q167128 SMS: Network Ports Used by Remote Helpdesk Functions
	
	For further information, see:
	
	  Q256884 TCP and UDP Ports Used by Remote Control Have Changed in SP2
	
	Other Related Information
	-------------------------
	
	
	
	
	Additional query words: prodsms netbt
	
	======================================================================
	Keywords          : kbsetup kbConfig kbsms200 smssetup smsconfig smssenders kbSMSSender 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
