---
layout: post
title: "Including Javascript File From Another Javascript File"
description: "Including Javascript file from another Javascript File"
category: Javascript
tags: [Javascript]
---
{% include JB/setup %}

## The Idea

We usually add some Javascript to a file by embeding it directly into a HTML file, like this

	<script type="text/javascript" src="script/jquery.min.js"></script>

We can actually add it from another Javascript file for example `testing.js`

## The Logic

We have to create a `script` object that will contains the Javascript source that we want to add

		var script  = document.createElement('script');
   		script.src  = 'script/jquery.min.js';
   		script.type = 'text/javascript';

After creating it, we want it to be included on the `Head` part of a HTML file that we will put our `testing/js`. This can easily done by using `document.getElementsByTagName`

		document.getElementsByTagName('head').item(0).appendChild(script);

## The Problem

Javascript is a asynchronous programming language which means it doesn't run in a straight way from top to bottom.

If we implement our code just as it is and tried to use functions that are existed in the included Javascript file, our browser won't recognized the function. This happened because of the asynchronous characteristic of Javascript.

Instead of waiting for the code to be loaded, Javascript will just continue with the next line of code in our `testing.js` in which we call functions in a Javascript file which still not finished loading.

To solve the problem, we will let the Javascript file to be loaded before calling the function.

## The Code

This is the final code for the file. As you can see, we will put our codes on script's onload. This will make sure the code has finished loaded before calling it's functions.

	function include(file){
  		var script  = document.createElement('script');
   		script.src  = file;
   		script.type = 'text/javascript';
   		script.defer = true;
   		script.onload= function(){
      		$(document).ready(function() {
      			'add your code here
      		})
      	}

   		document.getElementsByTagName('head').item(0).appendChild(script);
 	}
 
 	//add jQuery
	include('script/jquery.min.js');
