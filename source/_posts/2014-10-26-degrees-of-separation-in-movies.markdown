---
layout: post
title: "Degrees of Separation in Movies"
date: 2014-10-26 20:36:15 -0400
comments: true
categories: [Python,SQL,SQLite,degrees of separation,movies,The Wizard of Oz,Nicolas Cage,Homestuck]
---

Here's a fun fact for you: 91% of all movies are within six degrees of separation from each other.

According to IMDb, anyway.

I recently wrote a script in Python to search through a [snapshot of IMDb](http://www.imdb.com/interfaces) for how many movies are within six degrees of separation from "The Wizard of Oz". Any movie that shared an actor with "The Wizard of Oz" is degree 1, and any movie that shared an actor with a movie that shared an actor with "The Wizard of Oz" is degree 2, etc... The snapshot uses the following SQLite schema:

{% codeblock %}
CREATE TABLE Actor (
    aid INTEGER PRIMARY KEY AUTOINCREMENT,
    first TEXT DEFAULT '',
    last TEXT DEFAULT '',
    dob DATE DEFAULT '',
    gender TEXT DEFAULT '');

CREATE TABLE Movie (
    mid INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT DEFAULT '',
    year INTEGER DEFAULT 0,
    rating TEXT DEFAULT '');

CREATE TABLE Role (
    aid INTEGER REFERENCES Actor(aid),
    mid INTEGER REFERENCES Movie(mid),
    role TEXT DEFAULT '',
    billing INTEGER DEFAULT 0);
{% endcodeblock %}

Here's the percent of all movies within 6 degrees:

<img src="{{ root_url }}/images/2014-10-26-degrees-of-separation-in-movies/fig1.png" style="width:50%; height:50%"/>

When I saw this I started to wonder what percent of movies is "The Wizard of Oz" connected to for any degree number? I ran the code again for 15 degrees this time, and it looks like it tops out at about 91%...

<img src="{{ root_url }}/images/2014-10-26-degrees-of-separation-in-movies/fig2.png" style="width:50%; height:50%"/>

Well that's cool I guess, but let's look at other movies! I'm sure you're all wondering how well connected Nicolas Cage is – I have a bit of a soft spot for [Con Air](http://www.mspaintadventures.com/?s=6&p=003831).

<img src="{{ root_url }}/images/2014-10-26-degrees-of-separation-in-movies/fig3.png" style="width:50%; height:50%"/>

After looking around at a few other movies, it seems like all of them top out at 91% after degree 4 or so. I guess this means that 9% of the movies on IMDb star actors who are not even remotely famous. You can find my code [here](https://github.com/stevengt/Misc.-Small-Projects/blob/master/degreesOfSeparation.py), let me know if you find any other cool trends!

<img src="{{ root_url }}/images/2014-10-26-degrees-of-separation-in-movies/cage.jpg" style="width:40%"/>

