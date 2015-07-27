---
layout: post
title: "DateTime TimeZone conversion with Joda in Scala"
description: "datetime timezone conversion with Joda in Scala"
category: Scala
tags: [Scala, Joda, backend]
---
{% include JB/setup %}

## The problem

I need to convert a UTC DateTime to Local TimeZone in PlayFramework Scala and vice versa.

## The Methods

Converting from UTC to a specific timezone is simple, you can use `.withZone`. So, this is the method I used for `UTC to Local TimeZone`. And yes, I know its some crappy error handling LOL

{% highlight scala %}

def convertUtcToTimeZone(dateTime: DateTime, timeZone: String) =
	Try(dateTime.withZone(DateTimeZone.forID(timeZone))) getOrElse dateTime.withZone(DateTimeZone.forID("Etc/UTC"))

{% endhighlight %}

The real bussiness is on converting from local TimeZone to UTC. I need to parse the passed DateTime which timestamp is on UTC to date time with local timezone stamp. I used `LocalDateTime` for the purpose. It changed the date time timezone stamp without changing the value. I was using `.convertLocalToUTC` before but its not consistent.

So, here's the meat. And my usual crappy error handling

{% highlight scala %}

def convertTimeZoneToUtc(dateTime: DateTime, timeZone: String) = {
    Try {
      val zone = DateTimeZone.forID(timeZone)
      val localDateTime = new LocalDateTime(dateTime).toDateTime(zone)
      localDateTime.withZone(DateTimeZone.UTC)
    } getOrElse dateTime
}
	
{% endhighlight %}

