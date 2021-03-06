---
layout: page
title: "Q233550: Component Builder Appears to Change Component's Transaction ID"
permalink: /kb/233/Q233550/
---

## Q233550: Component Builder Appears to Change Component's Transaction ID

{% raw %}

	Article: Q233550
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0 SP2,4.0SP2
	Operating System(s): 
	Keyword(s): kbsna400sp2
	Last Modified: 05-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft COM Transaction Integrator for CICS and IMS, version 4.0 SP2 
	- Microsoft SNA Server, version 4.0SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you design COM Transaction Integrator for CICS and IMS (COMTI) components
	using Component Builder (CB), it may seem possible to change the "Transaction
	ID" of a locked method. However, when you save the component, the presumed
	change does not persist.
	
	In some cases, when a method is locked, the edit box for the Transaction ID in
	the Host Names properties is not disabled. At the same time, the title for the
	edit box, Transaction ID, is grayed out. Component Builder allows changing the
	Transaction ID value in the edit box. Then, if the dialog box is closed and
	reopened, the Transaction ID is restored to its original value.
	
	If you do not make that check, you might save the component library and test with
	it. The testing would be confounded because the Transaction ID would not be set
	to the new value.
	
	One place in particular that this could cause a problem is after you have used
	the Import COBOL Wizard of Component Builder to create a new method in a
	component library. After this process, the method is in the "Locked" state.
	Nevertheless, the Transaction ID edit box is enabled, and you can change the
	value of the Transaction ID. However, as above, the change is not persistent.
	
	WORKAROUND
	==========
	
	If the component is installed in an Microsoft Transaction Server (MTS) package,
	delete it by taking these steps:
	
	1. Right-click My Computer in MTS Explorer, and click Shut Down Server
	  Processes.
	
	2. Select the Components folder of the appropriate MTS package, right-click the
	  component, and click Delete.
	
	Then change the Transaction ID:
	
	1. Start the Component Builder, and open the component library.
	
	2. Right-click the method name, and click Unlock.
	
	3. Right-click the method name, and click Properties.
	
	4. Click the Host Names tab.
	
	5. Change the Transaction ID to the appropriate value.
	
	6. Close the dialog box, and lock the method again.
	
	7. Save the component library.
	
	8. Reinstall the component library in its MTS package.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version
	4.0.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna400sp2 
	Technology        : kbAudDeveloper kbSNAServSearch kbCOMTISearch kbCOMTI400SP2
	Version           : WINDOWS:4.0 SP2,4.0SP2
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
