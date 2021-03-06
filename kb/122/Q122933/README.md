---
layout: page
title: "Q122933: Event Viewer Messages for the Olicom Network Card"
permalink: /kb/122/Q122933/
---

## Q122933: Event Viewer Messages for the Olicom Network Card

{% raw %}

	Article: Q122933
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.5 
	- Microsoft Windows NT Server version 3.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	All error messages and/or warnings posted by the Olicom MAC driver have the
	Source field set to "OcTk16" or "OcTk32" depending on the adapter installed.
	
	System error messages, related to the Olicom MAC driver, may occur with different
	source names, i.e. "Service Control Manager".
	
	The messages are enumerated by the Event field and are described below in Event
	number order. You can display the message description, by highlighting the
	message and pressing ENTER.
	
	MORE INFORMATION
	================
	
	Event    Description
	
	--------------------
	
	 1      Bring-up diagnostics failed for OcTk1601.
	
	  Action: The adapter failed during the bring-up diagnostics. Shut down
	     your system and retry the operation. If the error persists, contact
	     your place of purchase.
	
	 2      Adapter initialize failed for OcTk1601.
	
	  Action: The adapter failed the initialization phase. Shut down your
	     system and retry the operation. If the error persists, contact your
	     place of purchase.
	
	 3      Adapter Check on OcTk1601.
	
	  Action: A serious error occurred on the adapter, causing an Adapter
	     check code to be posted. Restart your system. If the error persists,
	     contact your place of purchase.
	
	 4      Could not open adapter OcTk1601. Ring beaconing. Check network
	        speed settings.
	
	  Action: The network speed settings is wrong. Change it and restart your
	     system.
	
	 5      Could not open adapter OcTk1601. Duplicate node address.
	
	  Action: A duplicate address has been discovered on the ring. Change your
	     locally administered address and restart your system.
	
	 6      Could not open adapter OcTk1601. Request initialisation failed.
	
	  Action: An error occurred during adapter initialisation. Restart your
	     system. If the error persists, contact your place of purchase.
	
	 7      Could not open adapter OcTk601. Remove station received.
	
	  Action: The adapter has been removed by a LAN Manager station. Contact
	     your network administrator.
	
	 8      Could not open adapter OcTk1601.
	
	  Action: The adapter failed to open. Please check cables and connections
	     and retry the operation.
	
	 9      Could not download code on adapter OcTk1601.
	
	  Action: The download operation failed. Contact your place of purchase.
	10      Lobe wire fault detected by OcTk1601. Please check cable
	        connections.
	
	  Action: Check all cables and connections and try another lobe media
	     cable. Retry the operation.
	
	11      OcTk1601 has failed the lobe wrap test resulting from the beacon
	        auto-removal process and has deinserted from the ring.
	
	  Action: The adapter has deinserted from the ring, because the ring was
	     beaconing. Check the network speed settings and cable connections and
	     retry the operation. If the persists, contact your network
	     administrator.
	
	12      OcTk1601 has received a remove ring station Mac frame request and
	        has deinserted from the ring.
	
	  Action: The adapter has been removed by a LAN Manager station. Contact
	     your network administrator.
	
	13      The detected adapter for OcTk1601 is not supported by this driver.
	
	  Action: You have installed a wrong MAC driver for the adapter used.
	
	14      The configuration read for OcTk1601 is invalid.
	
	  Action: A configuration entry is invalid. Use the network control panel
	     to setup proper adapter settings.
	
	15      OcTk1601 has received a Trace Tool Remove frame from a Network
	        Management station and has disabled the packet filter.
	
	  Action: The adapter driver has cleared the PROMISCUOUS packetfilter bit,
	     as instructed by a LAN Manager station. Contact your network
	     administrator.
	
	5000    OcTk1601 : Has encountered a conflict in resources and could not
	        load.
	
	  Action: Check the resources used by the network adapter(s) ensure, that
	     no conflicts exists.
	
	5001    OcTk1601 : Could not allocate resources necessary operation.
	
	  Action: The driver failed to load, because it tried to allocate too many
	     resources. Decrease the number of receive and/or transmit buffers and
	     retry the operation.
	
	5002    OcTk1601 : Has determined that the adapter is not functioning
	        properly.
	
	  Action: The adapter could not be found or is not properly. Check I/O
	     base settings and retry the operation.
	
	5003    OcTk1601 : Could not find an adapter.
	
	  Action: The adapter could not be found by the MAC driver. Check I/O base
	     settings and retry the operation.
	
	5004   OcTk1601 : Could not connect to the interrupt number.
	
	  Action: The interrupt is already used by another device. Change the
	     adapter interrupt number and retry the operation.
	
	5005    OcTk1601 : Has encountered an internal error and has failed.
	
	  Action: An internal error has been discovered. Contact your place of
	     purchase.
	
	5006    OcTk1601 : The version number is incorrect for this driver.
	
	  Action: The driver version is incorrect. Contact your placeof purchase.
	
	5007    OcTk1601 : Timed out during an operation.
	
	  Action: A time-out error occurred. Contact your place of purchase.
	
	5008    OcTk1601 : Has encountered an invalid network address.
	
	  Action: An invalid network address was specified. Change the locally
	     administered network address and restart your system.The driver uses
	     the burned-in address when loading.
	
	5009    OcTk1601 : Does not support the configuration supplied.
	
	  Action: An invalid configuration entry was discovered. Use the network
	     control panel to set proper adapter parameters.
	
	5010    OcTk1601 : The adapter has returned an invalid value to the
	        driver.
	
	  Action: An internal error has occurred. Contact your place of purchase.
	
	5011    OcTk1601 : A required parameter is missing from the Registry.
	
	  Action: A parameter necessary for operation has been omitted in the
	     Registry. Use the network control panel to set properparameters.
	
	5012    OcTk1601 : The IO Base Address supplied does not match the jumpers
	        on the adapter.
	
	  Action: The adapter could not be found by the MAC driver. Check I/O base
	     settings and retry the operation.
	
	5014    OcTk1601 : The adapter is disabled. The driver cannot open the
	        adapter.
	
	  Action: Make sure the startup parameter for the Olicom Token Ring
	     adapter driver is set to "Manual". Use the "Devices" applet in the
	     control panel to change the settings.
	
	5015    OcTk1601 : There is an I/O port conflict.
	
	  Action: The ports used by the MAC driver is already in use by another
	     device. Change the I/O Base address for the adapter.
	
	5016    OcTk1601 : There is an I/O port or DMA channel conflict.
	
	  Action: Check the I/O port and DMA usage by the adapter to ensure that
	     there is no resource conflicts.
	
	5017    OcTk1601 : There is a memory conflict at address xx.
	
	  Action: The MAC driver and another device could not share memory.
	
	5018    OcTk1601 : There is a interrupt conflict at interrupt number xx.
	
	  Action: Change the interrupt selection on the adapter and retry the
	     operation.
	
	5019    OcTk1601 : There is a resource conflict at DMA channel xx.
	
	  Action: Change the DMA channel selection on the adapter andretry the
	     operation.
	
	If you experience any problems, you should write down the "Event ID", "Source",
	"Description" and "Data" fields in the "Event Detail" window.
	
	REFERENCES
	==========
	
	README.TXT in the \\DRVLIB\NETCARD\X6\OCTK16
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search
	Version           : winnt:3.5
	
	=============================================================================
	

{% endraw %}
