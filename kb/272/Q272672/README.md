---
layout: page
title: "Q272672: XIMS: Internet Mail Service Does Not Generate NDR Message"
permalink: /kb/272/Q272672/
---

## Q272672: XIMS: Internet Mail Service Does Not Generate NDR Message

{% raw %}

	Article: Q272672
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	A message in the Imcdata\In folder may never be delivered and may remain in that
	folder. If you stop and restart the Exchange Server Internet Mail Service, the
	message may be redelivered to most of the recipients of the message.
	
	The following event ID 4120 error message is logged in the application event
	log:
	
	  Event ID: 4120
	  Type: Error
	  Source: MSExchangeIMC
	  Category: Internal Processing
	
	  Description:
	  In the process of creating a notification of delivery failure to the sender of
	  a message, an error occurred causing the notification to be aborted. The
	  sender will not be informed that his original message failed to be
	  delivered.
	
	  Data:
	  0000: 9a 01 02 00 0e 00 07 80 ?......?
	  0008: 54 47 34 35 43 4c 50 36 TG45CLP6
	  0010: 00 .
	
	The following event ID 4131 error message may be logged in the application event
	log as well:
	
	  Event ID: 4131
	  Type: Information
	  Source: MSExchangeIMC
	  Category: Internal Processing
	
	  Description:
	  An unexpected error occurred in the Internet Mail Service. Information about
	  this error is stored in the data portion of this event.
	
	  Data:
	  0000: 3e 02 01 00 0e 00 07 80 >......?
	  0008: 54 47 34 35 43 4c 50 36 TG45CLP6
	  0010: 00
	
	CAUSE
	=====
	
	This problem can occur if the message has more than 32,766 (0x7FFE in
	hexadecimal numbers) recipients defined. The Internet Mail Service uses
	Messaging Application Programming Interface (MAPI) to create non-delivery report
	(NDR) messages, and attempts to add the recipients to an NDR message that MAPI
	is creating. MAPI uses the Emsmdb32.dll file to communicate with the information
	store, and the Emsmdb32.dll file has a limit of 32,766 recipients defined for
	the number of recipients on a single message.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server version 5.5 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Internet Mail Service
	
	+----------------------------+
	| File name    | Version     | 
	+----------------------------+
	| Msexcimc.exe | 5.5.2654.14 | 
	+----------------------------+
	| Imcmsg.dll   | 5.5.2654.14 | 
	+----------------------------+
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	MORE INFORMATION
	================
	
	This fix has two parts and addresses both the message that is already in the
	Imcdata\In folder and new messages that arrive to the Internet Mail Service with
	more than 32,766 recipients.
	
	For the message in the Imcdata\In folder, the basic problem is the inability to
	create an NDR because of the number of recipients. This fix creates the NDR with
	32,766 recipients and does not show the rest in the NDR. The following new event
	ID has been created to report this exceptional circumstance:
	
	  Event ID: 3041
	  Type: Warning
	  Source: MSExchangeIMC
	  Category: Internal Processing
	
	  Description:
	  Unable to deliver mail to all recipients. The total number of recipients
	  exceeds 32766.
	
	If a new message is delivered to the Internet Mail Service, the server sends a
	452 response when the number of recipients being submitted exceeds 0x7FFE. This
	response is an indicator to the sender that another message needs to be
	submitted with the remaining recipients (in other words, that the sender needs
	to break the message into multiple messages with fewer recipients on each
	message).
	
	  Up to 0x7FFE recipients the SMTP Command/Reponse pair would look like this:
	
	  SMTP: Command = RCPT TO: USER@MAIL.COM
	  SMTP: Response = 250 OK - Recipient <USER@MAIL.COM>
	
	  For every recipient after this, the following command/response pair would result:
	
	  SMTP: Command = RCPT TO: TOOMANY@MAIL.COM
	  SMTP: Response = 452 Requested action not taken: Exceed Recipient Limit
	
	Additional query words: Too Many Recipients IMS
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP5fix 
	Component         : IMC IMS Transport TransportCore
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
