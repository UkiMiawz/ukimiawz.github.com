---
layout: post
title: "Adding GET Parameter to Javascript File"
description: "Adding GET parameter to Javascript file"
category: Javascript
tags: [Javascript]
---
{% include JB/setup %}

## The Idea

In php files, it is common to assign a GET parameter like this

	testing.php?1234

What if we want to do the same thing with Javascript file? 
For example 

	testing.js?1234

## The Logic

Eventhought there is no actual function in Javascript to get a GET parameter when the file called, we can actually tricked it a little :

1. get the whole URL
2. split the values by `?` characters

## The Code

is actually	quite simple

	var passedId = requestURL.split('?')[1];

Here, we're splitting the string and since our file name is `testing.js?1234`, our split function will resulting in an array :

	[0] testing.js
	[1] 1234

Since we want to took the `1234` value, we took the value in index 1 of the array

## Next?

If you want to add more than 1 parameters, you can create a function to split and detecting the parameter name and parameter value. 

Me is currently too lazy to give some example *snore*
*kicked*