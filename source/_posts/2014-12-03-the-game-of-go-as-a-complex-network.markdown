---
layout: post
title: "The Game of Go as a Complex Network"
date: 2014-12-03 20:45:53 -0500
comments: true
categories: Go, Google Matrix, Pagerank, Georgeot, Giraud, Complex Networks, Python
---

I wrote some code in Python to construct a Pagerank vector of moves in the game of Go. Georgeot and Giraud discuss this method in their [paper](http://arxiv.org/abs/1105.2470) but do not include any sample code, so I decided it would be fun to implement it myself and run it on some sample data from the [K Go Server](http://www.u-go.net/gamerecords/).

The code on my [GitHub](https://github.com/stevengt/Go-Network) should be a good starting point if you're looking to construct a network of moves in Go, although there are some differences in my implementation and the one used by Georgeot and Giraud – for example, I do not take into account all the symmetries of plaquettes that they do. Here is a comparison of the top ten moves for λ<sub>1</sub>.

<img src="{{ root_url }}/images/2014-12-03-the-game-of-go-as-a-complex-network/go.png" style="width:65%; height:65%"/>
