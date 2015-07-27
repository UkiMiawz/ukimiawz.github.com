---
layout: post
title: "Parsing and adding URL parameters with JQuery"
description: "simple explanation to kanban"
category: Javascript
tags: [Javascript, URL Parse]
---
{% include JB/setup %}

## The Problem

I need to add new parameter to a URL with parameters listed in it. I can just add it via string but I also need to check the value of one of the parameters in the URL.
So, I have to get all the parameters attached, do some value checking on them, add new parameter, generate new URL with parameter added.

## The Important Bits

This is the method that I use to extract parameters from URL and turned them into array.

{% highlight javascript %}

function getURLParameters(url){

    var result = {};
    var searchIndex = url.indexOf("?");
    if (searchIndex == -1 ) return result;
    var sPageURL = url.substring(searchIndex +1);
    var sURLVariables = sPageURL.split('&');
    for (var i = 0; i < sURLVariables.length; i++)
    {       
        var sParameterName = sURLVariables[i].split('=');      
        result[sParameterName[0]] = sParameterName[1];
    }
    return result;
}

{% endhighlight %}

And here's how I use it to process my URL

{% highlight javascript %}

var url = document.createElement('a');
url.href = currentUrl;
var params = getURLParameters(currentUrl);

//do some checking
if(params["isParam"]) 
	//add new param
	params["newParam"] = "someValue";

var newUrl = url.origin + url.pathname + "?" + $.param(params);

{% endhighlight %}

