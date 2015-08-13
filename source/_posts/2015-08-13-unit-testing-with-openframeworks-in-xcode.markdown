---
layout: post
title: "Unit Testing with OpenFrameworks in XCode"
date: 2015-08-13 11:49:10 -0400
comments: true
categories: XCode, OpenFrameworks, unit testing
---

I had to struggle unnecessarily to set up unit testing with an OpenFrameworks project in Xcode. If you are inpatient like me and don't mind a bit of a hacky solution here are the steps I used.

<!-- more -->

<ol>
	<li>Add a test target named "tests" to your project.
	<li>Add <a href="http://cxxtest.com/">CxxTest-4.3</a> to your source root folder and add its location to the header search paths.
	<li>Create your unit tests in the "tests" target.
	<li>Create the following shell script in your source root folder and name it "cxxtest.sh".
	
		{% codeblock %}
		#!/bin/bash
	# cxxtest script
	./cxxtest-4.3/bin/cxxtestgen --error-printer -o ./cxxtest-4.3/bin/runner.cpp ./tests/*
	perl -pi -w -e 's/<cxxtest\//</g;' ./cxxtest-4.3/bin/runner.cpp
	rm ./cxxtest-4.3/bin/runner
	g++ -std=c++11 -stdlib=libc++ -o ./cxxtest-4.3/bin/runner  -I ./cxxtest-4.3/cxxtest/ -I ./src/ ./cxxtest-4.3/bin/runner.cpp
	./cxxtest-4.3/bin/runner
		{% endcodeblock %}

</ol>

If everything is set up right you should see the following result when you run "cxxtest.sh" in the terminal!

{% codeblock %}
	Running cxxtest tests (1 test).OK!
{% endcodeblock %}

The script creates "runner.cpp" from your tests, edits the include statements to match your project structure, and then compiles and runs the test. 

Hope this helps!
