---
layout: post
title: "CSS Full Background"
description: "CSS Full Background"
category: CSS-Tricks
tags: [CSS-Tricks]
---
{% include JB/setup %}

There are several ways to do this, this blog post have an excellent explanation

<a href="http://css-tricks.com/perfect-full-page-background-image/" target="_blank">Perfect Full Background Image</a>

Since I'm a lazy potatogrammer, I'll use CSS 3 for the trick

	html {
		background: url(img/background.jpg) repeat center center fixed;
		-webkit-background-size: cover;
		-moz-background-size: cover;
		-o-background-size: cover;
		background-size: cover;
	}