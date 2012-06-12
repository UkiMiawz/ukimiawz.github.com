---
layout: post
title: "XAML Binding   ListBox to ListCollection"
description: "Binding ListCollection to ListBox XAML"
category: XAML
tags: [.Net, XAML]
---
{% include JB/setup %}

The basic binding in XAML
We're using DataTemplate here

##The Idea

The idea is :

1. We got a `parent` class
2. Parent got `childList` of `child` class
3. `child` class got `ChildDateProperty` and `ChildStringProperty`

4. We got a listBox in the XAML
5. On the listbox items, we want the data in the line to be

	 `ChildDateProperty` : `ChildStringProperty`

For example :

	21 June 2012 : Here is testing entry

##The Code

Therefore, we're going to use ItemTemplate and DataTemplate for the binding

Here are the labels that we're going to use to display the data. We're binding them to the child's properties

	<Label Content="{Binding Path=.ChildDateProperty, StringFormat={}{0:dd MMMM YYYY HH:mm:ss}}"></Label>
	<Label Content=" : "></Label>
	<Label Content="{Binding Path=.ChildStringProperty}"></Label>

We're putting them into a `StackPanel` so it will stack nicely on a list item line. `StackPanel` stack items vertically as default, we want it the data to be on the same line, therefore we'll set the `StackPanel` orientation to `Horizontal`

 	<StackPanel Orientation="Horizontal">
	    <Label Content="{Binding Path=.ChildDateProperty, StringFormat={}{0:dd MMMM YYYY HH:mm:ss}}"></Label>
	    <Label Content=" : "></Label>
	    <Label Content="{Binding Path=.ChildStringProperty}"></Label>
	</StackPanel>

Put it in DataTemplate

	<DataTemplate>
	    <StackPanel Orientation="Horizontal">
	        <Label Content="{Binding Path=.ChildDateProperty, StringFormat={}{0:dd MMMM YYYY HH:mm:ss}}"></Label>
	        <Label Content=" : "></Label>
	        <Label Content="{Binding Path=.ChildStringProperty}"></Label>
	    </StackPanel>
	</DataTemplate>

Put it as ItemTemplate

	<ListBox.ItemTemplate>
	    <DataTemplate>
	        <StackPanel Orientation="Horizontal">
	            <Label Content="{Binding Path=.ChildDateProperty, StringFormat={}{0:dd MMMM YYYY HH:mm:ss}}"></Label>
	            <Label Content=" : "></Label>
	            <Label Content="{Binding Path=.ChildStringProperty}"></Label>
	        </StackPanel>
	    </DataTemplate>
	</ListBox.ItemTemplate>

Put the ItemTemplate to ListBox, bind the parent into `ItemsSource` and we're done!!

	<ListBox ItemsSource="{Binding ParentClass.ChildList}" Height="100" Width="370" HorizontalAlignment="Stretch" ClipToBounds="True">
	    <ListBox.ItemTemplate>
	        <DataTemplate>
	          	<StackPanel Orientation="Horizontal">
	                <Label Content="{Binding Path=.ChildDateProperty, StringFormat={}{0:dd MMMM YYYY HH:mm:ss}}"></Label>
	                <Label Content=" : "></Label>
	                <Label Content="{Binding Path=.ChildStringProperty}"></Label>
	            </StackPanel>
	        </DataTemplate>
	    </ListBox.ItemTemplate>
	</ListBox>