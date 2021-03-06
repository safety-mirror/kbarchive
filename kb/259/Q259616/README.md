---
layout: page
title: "Q259616: XFOR: Outlook Rules May Not Start on Internet Mail"
permalink: /kb/259/Q259616/
---

## Q259616: XFOR: Outlook Rules May Not Start on Internet Mail

{% raw %}

	Article: Q259616
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	Microsoft Outlook rules (for example, rules that automatically forward or reply
	to an e-mail message) may not start on messages that are received from the
	Internet.
	
	This issue generally occurs with rules that act as a result of the recipient of
	the message (the filter to determine whether the rule starts on a particular
	e-mail message is dependant on the recipient).
	
	This behavior occurs with recipients who have mailboxes that reside on the same
	computer that the Internet Mail Service is on (the Internet Mail Service that
	received the e-mail message). This behavior is typically seen on single-server
	installations, or in organizations that use site connectors over the Internet
	Mail Service.
	
	CAUSE
	=====
	
	This issue can occur because Outlook rules that are configured to act when the
	recipient matches certain criteria (for example, if the e-mail message has the
	recipient in the To line) actually check for the Exchange Server Distinguished
	Name (DN) in the MAPI properties of the e-mail message.
	
	When an e-mail message arrives from the Internet, and the e-mail message is
	destined for a local recipient (on the same server), the e-mail message is
	delivered locally, and the message transfer agent (MTA) does not touch the
	e-mail message.
	
	Normally, the MTA performs the resolution from Simple Mail Transfer Protocol
	(SMTP) proxy address (the address that the e-mail message was sent to over the
	Internet) to the Exchange Server DN. If the e-mail message does not pass through
	the MTA, this resolution is not performed, and the rule does not start.
	
	WORKAROUND
	==========
	
	There are several ways to work around this issue:
	
	- You can use the client to work around this issue:
	
	   - When you create a rule, do not specify the recipient, but do specify a
	     portion of the name of the recipient that appears in both the Display name
	     and the SMTP proxy address.
	
	     For example, if a user's Display name is Kim Akers, and the user's SMTP
	     proxy address is kim.akers@microsoft.com, configure the rule to check for
	     a Recipient line that contains the following text:
	
	  akers
	
	- You can force messages through the MTA to work around this issue. Exchange
	  Server 5.5 Service Pack 1 and later allow you to journal messages. You can
	  use a feature that was added to support journaling to force the delivery of
	  messages through the MTA:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	  1. Start Registry Editor (Regedt32.exe).
	
	  2. Locate the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS\ParametersSystem
	
	  3. On the Edit menu, click Add Value, and then add the following registry
	     value:
	
	  Value Name: No Local Delivery
	  Data Type: DWORD
	  Value: 0x1
	
	  4. Quit Registry Editor.
	
	- You can force the Internet Mail Service to perform the directory lookup to
	  work around this issue. In Exchange Server 5.5 you can use the Internet Mail
	  Service ResolveP2 registry key to force the Internet Mail Service to resolve
	  P2 recipients (which include To addressees on other systems and Cc
	  addresses). In many cases this work around is the best option:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	  1. Start Registry Editor (Regedt32.exe).
	
	  2. Locate the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIMC\ParametersSystem
	
	  3. On the Edit menu, click Add Value, and then add the following registry
	     value:
	
	  Value Name: ResolveP2
	  Data Type: DWORD
	  Value: 0x1
	
	  4. Quit Registry Editor.
	
	For additional information about this registry value, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q174755 XFOR: ResolveP2 Registry Setting Expanded in Exchange 5.5
	
	Additional query words: fire
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
