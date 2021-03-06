---
layout: page
title: "Q282115: If more than 4 SAP Exchange Connectors are installed, mail stop"
permalink: /kb/282/Q282115/
---

## Q282115: If more than 4 SAP Exchange Connectors are installed, mail stop

{% raw %}

	Article: Q282115
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55sp3
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	In Exchange Server 5.5 Service Pack 2 (SP2), with more than four EDK connectors
	of the same type installed on the same computer, mail flows fine. After you
	apply Exchange Server 5.5 Service Pack 3 (SP3), if more than four EDK Connectors
	are installed, mail stops processing on all EDK Connectors.
	
	WORKAROUND
	==========
	
	To work around this issue, increase the following threads in the registry.
	Customers have been able to run eight EDK Connectors on an Exchange Server 5.5
	computer with SP3 (or later) installed by increasing these threads.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Increase the threads in the following registry keys (unless otherwise stated, all
	of these keys are found in the HKLM\SYSTEM\CurrentControlSet\Services hive, and
	all values are in hexadecimal format):
	
	  ..\MSExchangeIS\ParametersPrivate\Gateway In Threads=0x2
	  ..\MSExchangeIS\ParametersPrivate\Gateway Out Threads=0x2
	  ..\MSExchangeIS\ParametersSystem\Background Threads=0x60
	  ..\MSExchangeIS\ParametersSystem\Max Threads (Public+Private)=0x64
	  ..\MSExchangeMTA\Parameters\Concurrent XAPI sessions=0x32
	  ..\MSExchangeMTA\Parameters\Concurrent connections to X.400 gateways=0x12
	
	MORE INFORMATION
	================
	
	Registry Changes Defined
	------------------------
	
	Gateway In Threads and Gateway Out Threads:
	
	These settings are the number of threads that the information store creates on
	behalf of an EDK Gateway when the gateway logs on to the information store. The
	Gateway In Threads value moves messages from the message transfer agent (MTA) to
	the information store's MTS-OUT queue (destined for the gateway). The Gateway
	Out Threads value moves messages (coming in from the gateway) out of the
	information store's MTS-IN queue to the MTA for distribution. Therefore, if you
	increase the Gateway In Threads value, you increase the pipe between the MTA and
	the information store for outbound Internet Mail Service messages.
	
	Background Threads:
	
	This is the number of threads allocated to run background processes such as
	defragmentation of the stores.
	
	
	Max Threads:
	
	Any time that you add a thread to a registry setting under any information store
	key, you must increase the Max Threads setting accordingly.
	
	Concurrent XAPI sessions:
	
	Among other things, this value defines how many sessions can be open between the
	MTA and information store. By default, the Concurrent XAPI sessions value is set
	to 0x50.
	
	
	After you run the Exchange Server Performance Optimizer, the Concurrent XAPI
	sessions value may be set to 0x30. In this case, it is recommended that you set
	the registry value back to 0x50. To determine if the Concurrent XAPI sessions to
	the information store are being exhausted, add the following counter to a
	Performance Monitor chart:
	
	  Object 'MSExchangeMTA Connections'
	  Counter 'Associations'
	  Instances'Microsoft Private MDB'
	
	If delivery from the EDK Connector is sluggish, you may need to further increase
	the Concurrent XAPI sessions value and increase the private and public
	information stores' send and delivery threads.
	
	
	Concurrent connections to X.400 gateways:
	
	This value represents the maximum number of concurrent connections to remote
	X.400 MTAs. The default value for Concurrent connections to X.400 gateways is
	0x6. If you treat the SXC Connector as an additional X.400 gateway and increase
	this value to 0x18, you can help improve the performance of the SXC Connector.
	
	The settings that are making the difference here are actually the "Max Threads
	(Public+Private)" and "Background Threads". There are fewer available threads in
	Exchange 5.5 SP2, SP3, and SP4 due to additional features like virus scanning
	which use some of the threads that were previously allocated or store processes
	right out of the box. Increasing the Gateway In and Gateway Out threads doesn?t
	help unless enough total threads have been allocated. This is where the Max and
	Background threads come into play. In order to get up to eight EDK connectors
	working, it is necessary to m0dify the registry settings to the values shown
	above.
	
	For additional information about information store threads, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q234065 XGEN: Troubleshooting the MTA Queue to the Internet Mail Service
	
	  Q166621 XADM: Gateway Out Threads Not Set Correctly by Perfwiz.exe
	
	  Q234702 XGEN: MTA Queue to Information Store Processing Slowly
	
	
	
	For additional information about MTA threads, click the article numbers below to
	view the articles in the Microsoft Knowledge Base:
	
	  Q247782 XCON: Mail Transfer Slow Across Connectors, Event IDs 3120 and 9316
	  Appear
	
	  Q234702 XGEN: MTA Queue to Information Store Processing Slowly
	
	
	
	Additional query words: IS IMS
	
	======================================================================
	Keywords          : exc55sp3 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
