---
layout: post
title: "Printing on Green Bar Style Paper"
date: 2014-11-30 11:19:56 -0500
comments: true
categories: Command line, a2ps, Green Bar paper
---

I like to look at code on green bar style paper, where alternating rows are different colors, because it's easier to read. I don't own actual paper to print it on but I found a neat command line tool [here](http://www.perlmonks.org/bare/?node_id=391709) to export a program to a PostScript file with the appropriate styling. For example, using a2ps the following command will create a PostScript file that styles the program test.py .

a2ps --prologue=matrix -o test.ps test.py


