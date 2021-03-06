---
layout: page
title: "Q224592: XADM: Naming Exchange Servers to Optimize KCC Performance"
permalink: /kb/224/Q224592/
---

## Q224592: XADM: Naming Exchange Servers to Optimize KCC Performance

{% raw %}

	Article: Q224592
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The naming of Exchange Server computers within an Exchange Site influences the
	performance of the Knowledge Consistency Checker (KCC) and the amount of network
	traffic that the KCC creates.
	
	MORE INFORMATION
	================
	
	Each Exchange Server computer in a site runs a KCC check every three hours to
	verify its knowledge of other Exchange Server computers in the site. To verify
	this knowledge, an Exchange Server computer will contact another Exchange Server
	computer in the site to compare their information. Which Exchange Server
	computer is contacted depends on its alphanumeric name.
	
	For example, site A has six servers: ServerA through ServerF. ServerA's KCC will
	contact ServerB, ServerB's will contact ServerC, and so on. The last Exchange
	Server computer alphanumerically, ServerF, will contact the first Exchange
	Server computer, ServerA, creating a virtual ring. The closer this virtual ring
	is to the actual network topology, the less network traffic will be caused by
	the KCC.
	
	Extending the above example, if ServerA, ServerC, and ServerE are on one subnet,
	and ServerB, ServerD, and ServerF are on another subnet, one full KCC cycle will
	cross subnets six times, in the following order:
	
	1. ServerA across to ServerB.
	
	2. ServerB across to ServerC.
	
	3. ServerC across to ServerD.
	
	4. ServerD across to ServerE.
	
	5. ServerE across to ServerF.
	
	6. ServerF across to ServerA.
	
	However, if the first subnet's servers are named ServerA, ServerB, and ServerC,
	and the second subnet's severs are named ServerD, ServerE, ServerF, one full KCC
	cycle will only cross subnets twice, in the following order:
	
	1. ServerC across to ServerD.
	
	2. ServerF across to ServerA.
	
	Generally, the more servers there are in a site, the larger the gains that will
	be made by naming Exchange Server computers as detailed above.
	
	More information on this subject can be found in Managing and Maintaining
	Microsoft Exchange Server 5.5 from Microsoft Press.
	
	Additional query words: intrasite replication
	
	======================================================================
	Keywords          :  
	Component         : Admin
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
