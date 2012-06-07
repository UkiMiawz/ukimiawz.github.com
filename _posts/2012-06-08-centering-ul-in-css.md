---
layout: post
title: "Centering UL in CSS"
description: "Centering UL in CSS"
category: CSS-Tricks
tags: [CSS-Tricks]
---
{% include JB/setup %}

Some time ago, I was having a trouble with centering UL element in HTML.
My UL is a horizontal type one, all LI set to float left and that way the UL don't have any height

It turns out I have to set the container text-align to center and display the ul element as inline-block
and voila!! It works~

#The HTML

	<div id="ulContainer">
		<ul>
			<li>Test</li>
			<li>Test1</li>
			<li>Test2</li>
			<li>Test3</li>
		</ul>
	</div>

#The CSS

	/*LIST*/

	#ulContainer
	{
		text-align: center;
	}

	#ulContainer ul
	{
		display: inline-block;
	    margin: 0;
	    padding: 0;
	    /* For IE, the outcast */
	    zoom:1;
	    *display: inline;
	}

	#ulContainer ul li
	{
		float:left;
		display: inline;
	}
