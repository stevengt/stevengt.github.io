---
layout: post
title: "Getting socket.io v1.x.x to Work on Heroku"
date: 2015-12-24 13:41:10 -0500
comments: true
categories: 
---

Many outdated tutorials will tell you that you need to add the below code to your server in order for socket.io code to work.

{% codeblock %}
io.configure(function () {
    io.set("transports", ["xhr-polling"]);
    io.set("polling duration", 10);
});
{% endcodeblock %}

However, in newer versions of socket.io (v1.x.x), the set() and configure() methods are deprecated, as outlined [here](http://socket.io/docs/migrating-from-0-9/#configuration-differences), and they result in the error "io.configure is not a function". Instead, you should pass in the settings when you initialize the instance, like this:

{% codeblock %}
var io = require('socket.io')({
    "transports" : ["xhr-polling"],
    "polling duration" : 10
}).listen(server); 
{% endcodeblock %}

That should be all you need to get your app running!