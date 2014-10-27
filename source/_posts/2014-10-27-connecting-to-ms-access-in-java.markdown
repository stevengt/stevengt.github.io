---
layout: post
title: "Connecting to MS Access in Java"
date: 2014-10-27 11:31:43 -0400
comments: true
categories: [java,odbc,jdbc-odbc,MS Access, jdk8, pypyodbc, ucanaccess, 64-bit, 32-bit, Microsoft Office]
---

Java has stopped supporting the JDBC-ODBC Bridge with the release of JDK 8, so here is my (somewhat quick and dirty) way of working with MS Access.

There are various alternatives you can try out such as [UCanAccess](http://ucanaccess.sourceforge.net/site.html), [PyPyODBC](https://code.google.com/p/pypyodbc/), or Easysoft's [API](http://www.easysoft.com/developer/languages/c/odbc_tutorial.html#pre_req). I've messed around with a few of these and I feel that they aren't quite as powerful as the bridge offered in previous versions of Java, and I don't have the time right now to improve my C skills enough for the particular project I'm working on.

My solution, which seems to work fine so far, is to install Java 7 alongside Java 8, and use the built in JDBC-ODBC bridge. If portability is a concern for you then maybe this isn't your best option, but for my purposes I'm fine with wrapping the code up in an executable.

If this is all you need to get set up, then great! I'm happy for you, I really am.

<img src="{{ root_url }}/images/2014-10-27-connecting-to-ms-access-in-java/happy.jpg" style="width:50%; height:50%"/>

I had trouble connecting to the ODBC driver, though, because I'm using 32-bit MS Office on a 64-bit system. If this is a problem for you, too, then installing the Microsoft ACE OLEDB Provider as outlined [here](http://blog.codefluententities.com/2011/01/20/microsoft-access-database-engine-2010-redistributable/) will help. Make sure you launch the installer from a command line with the "/passive" argument. Be wary that this might make Office behave strangely. I haven't noticed anything too bad so far, except that it now takes a minute or two to launch Office.

Hope this helps. This is a bit of a quick fix to meet a time constraint, so there are probably better ways to do this. If you have suggestions please share them below!




