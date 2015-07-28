---
layout: post
title: "Empty string validation in Scala"
description: "Empty string validation in Scala"
category: Scala
tags: [Scala]
---
{% include JB/setup %}

## Quick Note

Just a quick note before I forgot without even bumping my head on something.
This is codes that I used on play framework template for print index and checking for empty string.
You can add index to iteration by using `zipWithIndex` on a list, the index start from 0 as per usual

{% highlight scala %}

@for((imageUrl, index) <- imageUrls.zipWithIndex) {
  @if(imageUrl.exists(_.trim.nonEmpty)) {
    <br /><a href='@imageUrl' target="_blank">Image @(index + 1)</a>
  }
} 

{% endhighlight %}