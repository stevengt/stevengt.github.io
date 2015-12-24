---
layout: post
title: "Maven 'The forked VM terminated without saying properly goodbye' Error"
date: 2015-08-12 21:31:15 -0400
comments: true
categories: Maven, error, IntelliJ
---

I recently got this error while building a project in IntelliJ. It turns out the problem was related to improper capitalization of import statements in some of the files. If you get this error, try running the build with -x or -e to pin down where it is coming from and see if changing the import statements helps.
