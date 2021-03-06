---
layout: page
title: "Q113290: Epson ESCP/2 EPESCP2.DRV v. 1.60 Release Notes"
permalink: /kb/113/Q113290/
---

## Q113290: Epson ESCP/2 EPESCP2.DRV v. 1.60 Release Notes

{% raw %}

	Article: Q113290
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 28-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 3.1 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	The following is the text of the release notes that ship with the Epson ESCP/2
	driver, EPESCP2.DRV version 1.60, shipped by Epson.
	
	The information contained in this document is provided by Epson and has not been
	tested or confirmed by Microsoft.
	
	MORE INFORMATION
	================
	
	---------------------------------------------------------------------
	Epson Research Center
	Imaging Products Development
	
	Release Notes for
	MS Windows Mini Driver for Epson ESC/P 2 Printers
	
	EPESCP2.DRV ver 1.60
	
	February 4, 1994
	
	Product Description
	This is a release of an upgraded Windows driver which supports the
	latest Epson printer models and paper sizes.  It is a "Mini driver"
	which works in conjunction with the Microsoft Universal Printer Driver.
	The Mini Driver code and copyright for EPESCP2.DRV ver 1.6 are owned by
	Microsoft Corporation.  The Universal Printer Driver code and copyright
	are owned by Microsoft Corporation.  The copyright displayed in the
	driver's About box refers to the Universal Printer Driver and is
	"Microsoft Corporation".
	
	The following files are included in this release:
	
	EPESCP2.DRV       1/3/94    13699    (the Mini driver)
	OEMSETUP.INF    1/3/94    1332     (setup file)
	
	In addition, the following related files are required for a complete
	driver solution:
	UNIDRV.DLL      ver. 3.1.1 or later (the Universal driver)
	UNIDRV.HLP                          (help file)
	
	Version Update Description
	The differences between version 1.60 compared to the previous version
	1.5 are as follows:
	1)   Stylus 400 has been added.
	2)   Stylus 800+ has been added.
	3)   A2 paper size has been added to Stylus 1000
	
	Installation
	Use Control Panel / Printers to install these drivers.  Remove all
	previously installed version 1.0, 1.1, 1.3, 1.4, or 1.5  Epson ESC/P 2
	drivers before installing 1.6.
	Be sure to use Universal Printer Driver 3.1.1, 3.1.2, 3.1.4 or later.
	This Mini driver is not recommended for use with Universal Printer
	Driver 3.1.
	
	Deinstallation
	To deinstall the ESC/P 2 drivers, within the Control Panel / Printers
	dialog, highlight the driver name in the "Installed Printer" box, then
	click the Remove button.
	
	Usage
	Refer to Microsoft Windows documentation for use of printer drivers.
	
	Technical Limitations
	1)  Matching Paper Size with Paper Source
	It is very important that the correct Paper Source (Tractor, Sheet
	Feeder or Manual) be selected for each Paper Size.
	
	   a) Only the Fanfold paper sizes (sizes with the word Fanfold in
	      their name) can be used properly with the Tractor Paper Source.
	      Do not use any other Paper Sizes with the Tractor Paper Source.
	
	   b) All other paper sizes (including User Defined) can be used only
	      with the Manual or Sheet Feeder Paper Source.  Do not use any
	      Fanfold Paper Sizes with the Manual or Sheet Feeder Paper Source.
	
	Here is a complete list of which Paper Sizes can be used for each Paper
	Source:
	
	Tractor only                             Sheet Feeder or Manual only
	------------------------------------------------------------------------
	Letter Fanfold 8 1/2 x 11 in             Letter 8 1/2 x 11 in
	Fanfold 11 x 8 1/2 in                    Legal 8 1/2 x 14 in
	Fanfold 210 x 305 mm                     Statement 5 1/2 x 8 1/2 in
	A4 Fanfold 210 mm x 11 2/3 in            Tabloid 11 x 17 in
	Fanfold 358 x 305 mm                     A3 297 x 420 mm
	US Standard Fanfold 14 7/8 x 11 in       A3 420 x 297 mm
	                                        A4 210 x 297 mm
	                                        A5 148 x 210 mm
	                                        B4 250 x 354 mm
	                                        B5 182 x 257 mm
	                                        6 3/4 Envelope 3 5/8 x 6 1/2 in
	                                        Envelope #10 4 1/8 x 9 1/2 in
	                                        Envelope DL 110 x 220 mm
	                                        Envelope C5 162 x 229 mm
	                                        User Defined Size...
	                                        A2 420 x 594 mm
	
	If these simple and intuitive rules are not followed, the correct
	results cannot be assured.  The margins will be incorrect and the image
	will possibly spill over onto a second page.
	Matching the Paper Source with the Paper Size is a new requirement for
	version 1.5 and 1.6 which was not necessary on version 1.4.
	
	2)  User Defined Size
	Note that User Defined paper size is not to be used with the Tractor
	Paper Source.
	If User Defined Paper Size is selected while the Tractor Paper Source is
	selected, the user defined paper length will be ignored as the physical
	form length and the printer's maximum form length of 22 inches will be
	used.  At the end of each page, the printer will feed the paper as if it
	was a 22 inch form.  The command for the User Defined form length
	entered by the user cannot be sent to the printer.  This is a limitation
	of the Uni/Mini Driver.  There is no problem in Sheet Feeder or Manual
	mode, the paper will be correctly ejected.
	
	3)  B4 and B5 Paper Sizes
	There are two standards for defining B4 and B5 size paper.  This driver
	only supports the sizes which are standard in Windows.
	
	     Standard 1     Standard 2     Size used in Windows and this driver
	------------------------------------------------------------------------
	B4    250 x 354 mm   257 x 364 mm   250 x 354 mm
	B5    177 x 250 mm   182 x 257 mm   182 x 257 mm
	
	The differences seem to be between European and Japanese implementation
	of these paper sizes.  If using B4 or B5 paper, check that it matches
	the supported size in the driver.
	
	4)  Auto Print Direction
	The Auto Print Direction feature of the Stylus printer family is not
	supported by this driver.  It always prints in uni-directional mode.
	
	5) A2 Paper Size Printable Area
	Due to the limitation of the physical mechanism width, and a limitation
	of the printer command language length, the printable area on A2 paper
	is only 13.6 inches wide and 22 inches long.
	
	Application Notes
	1)  Universal Printer Driver
	These drivers require Universal Printer Driver 3.1.1, 3.1.2, 3.1.4 or
	later.  Only one Uni Driver can be installed at a time.  If you already
	have other printer mini drivers installed which require an earlier
	version of Uni Driver than the 3.1.1, 3.1.2, or 3.1.4 driver you are
	installing, then some incompatibilities may occur in those other printer
	mini drivers.  This is an issue with the Uni Driver / Mini Driver
	concept.
	
	2)  Setting Resolution
	Some applications such as Microsoft Write, require the resolution
	settings to be set in the Control Panel.  Setting a resolution in the
	Write Print dialog which conflicts with the Windows Control Panel
	setting may give unexpected results.
	
	3)  "Non-standard" Paper Sizes
	Some "non-standard" paper sizes are not fully recognized by some
	applications.  The sizes may not be listed in the Page Setup dialog.  To
	use these sizes, they must first be selected in the Windows Control
	Panel.  The paper size may then appear as "blank" in the application's
	Page Setup dialog.  The document can then be printed normally.  The
	following paper sizes are "non-standard":
	
	A3 420 x 297 mm
	Letter Fanfold 8 1/2 x 11 in
	Fanfold 11 x 8 1/2 in
	Fanfold 210 x 305 mm
	A4 Fanfold 210 mm x 11 2/3 in
	Fanfold 358 x 305 mm
	US Standard Fanfold 14 7/8 x 11 in
	6 3/4 Envelope 3 5/8 x 6 1/2 in
	Envelope #10 4 1/8 x 9 1/2 in
	Envelope DL 110 x 220 mm
	Envelope C5 162 x 229 mm
	
	4)  Ami Pro and Letter Paper Size
	There are two paper sizes in the driver that are 8 1/2 x 11 inches;
	Letter and Letter Fanfold.  When using Ami Pro, if the Letter button is
	selected in the Modify Page Layout dialog, Ami Pro will always select
	the Letter paper size regardless of the Paper Size selected in the
	driver (in Page Setup).  In this case, it is impossible to print using
	the Letter Fanfold paper size.  The result of using Letter is that the
	margins for Manual and Sheet Feeder will be used instead of the zero
	margins expected when using Letter Fanfold with a Tractor.  The
	resulting printout is acceptable unless the user absolutely requires
	zero margins.  If zero margins are required, select Custom Size in the
	Page Layout dialog and enter values such as 8.40 x 11.0 inches.  Then by
	selecting Tractor and Letter Fanfold in the driver, the proper zero
	margins will be used.  (Do not enter 8.50 x 11.0 inches, because AmiPro
	will still recognize this as Letter size paper and will still use the
	Manual and Sheet Feeder margins).
	
	5)  Margin Tolerances
	The driver margins have been minimized to as close to the physical
	margins in the printer specification as possible.  These margins include
	some tolerance for errors in the loading position, paper feeding
	accuracy, and paper length.  However, it is not practical to include
	enough tolerance to work in every possible situation.  It is possible
	that under certain conditions the driver margins will not be large
	enough to prevent errors such as the printed image exceeding the
	printable area of the sheet of paper and spilling over onto a second
	page.  If this occurs, the user should do the following:
	a)  Make sure the actual paper size is within one millimeter (0.04
	   inches) of its specification size.
	b)  Make sure the Paper Source correctly matches the Paper Size (see
	   Technical Limitations #1).
	c)  Increase the document's bottom margin in the application.
	
	6)  Microsoft Word 2.0 and 6.0
	It is possible for a General Protection Fault to occur when printing a
	document that has data in the unprintable area.  Only occurs on some
	documents.  It is not clear if this is an application problem or a
	driver problem.
	
	7)  A2 Paper Size with Microsoft Write
	The printable length of A2 paper size is only 22 inches (see Technical
	Limitations).  Write reports an incorrect value of 1.93 cm (0.76 inches)
	for the minimum bottom margin, but it should be 3.53 cm (1.39 in).  This
	error does not affect the actual printable area and does not cause any
	other problems.  This error has only been found on Microsoft Write, but
	may also occur on some other applications.
	
	
	Additional query words: gpf win31 Action Actionprinter LQ 570 870 1170 1070 plus 5000 5500 3250 100 Stylus 800 1000 300 400 + esc p2
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
