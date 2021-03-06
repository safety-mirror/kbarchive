---
layout: page
title: "Q139636: X400: Abbreviations for CCITT Recommendation X.224"
permalink: /kb/139/Q139636/
---

## Q139636: X400: Abbreviations for CCITT Recommendation X.224

{% raw %}

	Article: Q139636
	Product(s): Microsoft Mail For PC Networks
	Version(s): MS-DOS:3.0,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Gateway to X.400, versions 3.0, 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists some of the acronyms that are seen when you view the
	X400MMDD.LOG file, where mmdd represents the month (mm) and the day (dd) the log
	was written when debug (-LD) was enabled.
	
	MORE INFORMATION
	================
	
	Data Units
	----------
	
	  TPDU           Transport Protocol Data Unit
	  TSDU           Transport Service Data Unit
	  NSDU           Network Service Data Unit
	
	Types of Transport Protocol Data Unit
	-------------------------------------
	
	  CR TPDU        Connection Request TPDU
	  CC TPDU        Connection Confirm TPDU
	  DR TPDU        Disconnect Request TPDU
	  DC TPDU        Disconnect Confirm TPDU
	  DT TPDU        Data TPDU
	  ED TPDU        Expedited Data TPDU
	  AK TPDU        Data Acknowledge TPDU
	  EA TPDU        Expedited Acknowledge TPDU
	  RJ TPDU        Reject TPDU
	  ER TPDU        Error TPDU
	
	TPDU fields
	-----------
	
	  LI             Length Indicator (field)
	  CDT            Credit (field)
	  TSAP-ID        Transport Service Access Point Identifier (field)
	  DST-REF        Destination Reference (field)
	  SRC-REF        Source Reference (field)
	  EOT            End of TSDU mark
	  TPDU-NR        DT TPDU number (field)
	  ED-TPDU-NR     ED TPDU number (field)
	  YR-TU-NR       Sequence number response (field)
	  YR-EDTU-NR     ED TPDU number response (field)
	
	Time and associated variables
	-----------------------------
	
	  T1             Local retransmission time
	  N              The maximum number of retransmission's
	  L              Time bound on reference and sequence numbers
	  I              Inactivity time
	  W              Window time
	  TTR            Time to try reassignment/resynchronization
	  TWR            Time to wait for reassignment/resynchronization
	  TS1            Supervisory timer 1
	  TS2            Supervisory timer 2
	  MLR            NSDU lifetime local-to-remote
	  MRL            NSDU lifetime remote-to-local
	  ELR            Expected maximum transit delay local-to-remote
	  ERL            Expected maximum transit delay remote-to-local
	  R              Persistence time
	  AL             Local acknowledge time
	  AR             Remote acknowledge time
	
	Miscellaneous
	-------------
	
	  TS-user        Transport Service user
	  TSAP           Transport Service Access Point
	  NS-provider    Network Service Provider
	  NSAP           Network Service Access Point
	  QOS            Quality of service
	
	The information above was extracted from The International Telegraph and
	Telephone Consultative Committee (CCITT), Recommendation X.224, Section 4, page
	43. Please refer to Recommendation X.224 for a more in-depth definition and
	description.
	
	For additional information on the X400MMDD.LOG, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q86988 X400: How MTAs Initiate and Communicate
	
	
	Additional query words: 3.00 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbMailGateSearch kbZNotKeyword3 kbMailGatex400300 kbMailGatex400320
	Version           : MS-DOS:3.0,3.2
	
	=============================================================================
	

{% endraw %}
