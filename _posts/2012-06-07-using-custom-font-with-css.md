---
layout: post
title: "Using custom font with CSS"
description: "Using font face for custom font"
category: CSS-Tricks
tags: [CSS-Tricks]
---
{% include JB/setup %}

For more explanation : <a href="http://sixrevisions.com/css/font-face-guide/" target="_blank">Using Font Face</a>

The code is pretty simple, here is the basic code

	@font-face {  
	  font-family: "Eurostile";  
	  src: url(fonts/EurostileLTStd.eot); /* IE */  
	  src: local("Eurostile"), url(fonts/EurostileLTStd.otf) format("opentype"); /* non-IE */  
	} 

If you got bold variation for the font, you won't need to create another font family for it, simply add your font variation style into the css.

For example, bold text, simply add `font-weight: bold`

	@font-face {  
	  font-family: "Eurostile";  
	  font-weight:bold;
	  src: url(fonts/EurostileLTStd-Bold.eot); /* IE */  
	  src: local("Eurostile"), url(fonts/EurostileLTStd-Bold.otf) format("opentype"); /* non-IE */  
	}

IE can only read EOT file, <a href="http://www.fontsquirrel.com" target="_blank">FontSquirrel</a> got a perfect font-face kit generator for it.
The generator will generate not only EOT but also other type of font file.

<a href="http://www.fontsquirrel.com/fontface/generator" target="_blank">
<img style="background:#000000" src="/img/fontSquirell.png" alt="fontsquirrel" />
</a>

They also got nice collection of fonts, you should check their website!