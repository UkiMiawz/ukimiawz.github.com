---
layout: post
title: "XAML Using Border"
description: "XAML Using Border"
category: XAML
tags: [XAML, .Net]
---
{% include JB/setup %}

Unlike CSS, XAML elements don't have border property with them.
As a subtitute, we can use `Border` object tag before our XAML object
It works more or less same with CSS's border

	<Border 
       BorderThickness="4"
       BorderBrush="Red"
       Background="LightBlue"
       HorizontalAlignment="Center" 
       VerticalAlignment="Center"
       Width="140"
       Height="80">
        <Canvas>
            <TextBlock Canvas.Top="10" Canvas.Left="20">
     			Border sample
            </TextBlock>
        </Canvas>
    </Border>

Reference : <a href="http://www.longhorncorner.com/uploadfile/mahesh/xaml-border/" target="_blank">XAML-border</a>
