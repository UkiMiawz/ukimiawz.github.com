---
layout: post
title: "XAML Using String Format"
description: "XAML Using String Format"
category: XAML
tags: [XAML, .Net]
---
{% include JB/setup %}

You won't want those date viewed in some plain numbers won't you?
That's why we're using `StringFormat`!

Instead shown as '20/10/2011' it will shown nicely  as `20 October 2012`

One way is by using `ContentStringFormat`

	<Label
    	Content="{Binding Path=DateAsked}"
    	ContentStringFormat="{}{0:dd MM YYYY HH:mm:ss}" />

Another way is using `StringFormat` on binding

    <GridViewColumn 
   	 	Header="Order ID"
    	DisplayMemberBinding="{Binding Path=OrderID, StringFormat='{}{0:dd.MM.yyyy}'}" />

##Format List

Date

	<TextBlock Text="{Binding Date, StringFormat={}{0:MM/dd/yyyy}}" />

Date with Time

	<TextBlock Text="{Binding Date, StringFormat={}{0:MM/dd/yyyy hh:mm tt}}" />

Currency

	<TextBlock Text="{Binding Amount, StringFormat={}{0:C}}" />

Text in front of the currency

	<TextBlock Text="{Binding Amount, StringFormat=Total: {0:C}}" />

Reference : <a href="http://elegantcode.com/2009/04/07/wpf-stringformat-in-xaml-with-the-stringformat-attribute/" target="_blank">WPF String Format</a>