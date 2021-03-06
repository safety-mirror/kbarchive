---
layout: page
title: "Q247293: SMS: Server Discovery DDRs Flood Sites"
permalink: /kb/247/Q247293/
---

## Q247293: SMS: Server Discovery DDRs Flood Sites

{% raw %}

	Article: Q247293
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbtool kbsms200 kbsms200bug
	Last Modified: 23-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When excessive DDR files are created by the WINNT_SERVER_DISCOVERY discovery
	agent, it may cause backlogs in the Ddm.box file and in inter-site
	communications. Note that this issue is most severe in an environment with
	multiple sites in a single domain with logon installation or discovery enabled.
	
	CAUSE
	=====
	
	This problem can occur because WINNT_SERVER_DISCOVERY_AGENT is (by default)
	scheduled to run every day at 12:12 PM. This discovery agent generates a DDR for
	each site system in the site, and this data must be replicated to the parent
	site, possibly causing excessive inter-site traffic and producing an excessive
	load on the discovery data manager thread of the executive.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0 and is fixed in Service Pack 2. Server Discovery is now tied to
	Heartbeat Discovery and will run on its configured time interval.
	
	MORE INFORMATION
	================
	
	This issue is most severe in an environment with multiple sites in a single
	domain with logon installation or discovery enabled. In this situation, each
	domain controller is a site system for each site and as such, each site's
	WINNT_SERVER_DISCOVERY_AGENT creates a DDR for every domain controller in
	addition to the normal site systems. For example, if there are 100 BDCs and each
	BDC is a site server in the hierarchy, every site server creates a DDR for each
	of these BDCs, so all 100 sites generate at least 100 DDRs (which totals to
	10,000 DDRs daily). These DDRs will then be replicated up the hierarchy, causing
	additional inter-site traffic. One other aspect of this particular site design
	is that the DDRs generated will be larger than normal because there is an
	"agentinfo" field for every site that shares the logon point, and the larger
	DDRs are then processed at a slower rate than those which do not have the
	additional fields.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbtool kbsms200 kbsms200bug 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
