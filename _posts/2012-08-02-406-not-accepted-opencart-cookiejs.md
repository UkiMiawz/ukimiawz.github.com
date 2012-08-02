---
layout: post
title: "406 not accepted Opencart cookie.js"
description: "Opencart cookie function javascript error"
category: OpenCart
tags: [Opencart, CMS, ecommerce]
---
{% include JB/setup %}

## The symptoms

Upon opening an Opencart page I got a javascipt error which read something around

	Error 406 Not acceptible for catalog/view/javascript/jquery/ui/external/jquery.cookie.js

Which resulted on another error
	
	$cookie is not a function

Everything seems fine on my localhost @.@

## The problem

Some hosting server don't allows you to call a file with `cookie` phrase on it hence the `not accepted` error comes up

## The Fix

It turns out I only need to change the file name from `cookie.js` to `coookie.js` or any names you prefer.

Don't forget to change the `header.tpl` from

	<script type="text/javascript" src="catalog/view/javascript/jquery/ui/external/jquery.cookie.js"></script>

to 

	<script type="text/javascript" src="catalog/view/javascript/jquery/ui/external/jquery.coookie.js"></script>

