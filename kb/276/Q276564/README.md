---
layout: page
title: "Q276564: SMS: SMS Client Service Stops Responding (Hangs) During Startup"
permalink: /kb/276/Q276564/
---

## Q276564: SMS: SMS Client Service Stops Responding (Hangs) During Startup

{% raw %}

	Article: Q276564
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbnetwork kbClient kbConfig kbSecurity kbServer kbsms200 kbsms200bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a Systems Management Server (SMS) Client Services domain controller (DC)
	account "SMS&_<domaincontrollername>" is deleted, the SMS client
	service may stop responding (hang) during startup.
	
	CAUSE
	=====
	
	This behavior occurs because the Client Configuration Manager (CCM) account
	cleanup cycle runs every 30 days and deletes any SMS Client Services DC account
	when the domain controller cannot be contacted. This issue can occur frequently
	when multiple SMS-based site servers are sharing logon points from one master
	domain and when each server initiates an account cleanup cycle for which it sets
	the 30 day interval on its own.
	
	WORKAROUND
	==========
	
	To work around this issue, remove and then reinstall the SMS-based client on the
	domain controllers. This procedure temporarily resolves the issue until the next
	cleanup cycle runs.
	
	To prevent the cleanup cycle from running, change the registry on the SMS-based
	site server to set the date of the next account cleanup cycle to five years in
	the future:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. Start Registry Editor (Regedit.exe).
	
	2. Locate and click the following registry key:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Components\SMS_CLIENT_CONFIG_MANAGER\Next
	  Account Cleanup
	
	3. Change the value from 16\4\2000 to 16\4\2005. This example shows a date of
	  April 16, 2000.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	This behavior occurs mostly in multi-site shared domains when one of the domain
	controllers is offline. It can also occur if network problems are preventing
	access to one of the domain controllers.
	
	This can also occur in a single site domain with no logon points.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbnetwork kbClient kbConfig kbSecurity kbServer kbsms200 kbsms200bug 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
