---
layout: page
title: "Q40681: M.TMP Reset When Window Closed"
permalink: /kb/040/Q40681/
---

## Q40681: M.TMP Reset When Window Closed

{% raw %}

	Article: Q40681
	Product(s): See article
	Version(s): 1.00   | 1.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | mep buglist1.00 | mspl13_basic
	Last Modified: 15-MAY-1989
	
	Question:
	
	When I invoke the M editor, open a second window (arg F6 or arg arg
	F6), and close the first window (meta F6), my M.TMP file is reset. The
	only file in my M.TMP file is the one that I edited to perform this
	operation. Is there a way to prevent this from happening?
	
	Response:
	
	This phenomena occurs whenever you close a window that has had a file
	opened in it. Hence, if you open a file in the second window, then
	close the second window, M.TMP is reset. To avoid this behavior, don't
	close a window in which a file has been opened.
	
	Microsoft has confirmed this to be a problem in Version 1.00. We are
	researching this problem and will post new information as it becomes
	available.

{% endraw %}
