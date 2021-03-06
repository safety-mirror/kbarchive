---
layout: page
title: "Q27128: Cannot Debug Code in Overlays in Small or Compact Model"
permalink: /kb/027/Q27128/
---

## Q27128: Cannot Debug Code in Overlays in Small or Compact Model

{% raw %}

	Article: Q27128
	Product(s): See article
	Version(s): 2.10 2.20 2.30
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 14-AUG-1989
	
	Question:
	
	I have a C program, compiled with Microsoft C Version 5.00, which
	consists of several modules linked together as overlays. I am not able
	to trace into code in the overlays. I compiled in the default memory
	model. What is wrong?
	
	Response:
	
	The modules must be compiled in medium or large memory model to be
	overlaid. In the default model (small), or in the compact model, there
	is only one code segment, which cannot be overlaid. The main module is
	always resident and cannot be overlaid. You must use the compile
	option /AH, /AL, or /AM.

{% endraw %}
