---
layout: post
title: "XAML Multivalue command parameter binding"
description: ""
category: VB.Net
tags: [.Net, WPF, MVVM]
---
{% include JB/setup %}

This is what a common command parameter looks like. A button with a command parameter.

	<Button Content="Close" Command="{Binding Path=CloseCommand}" CommandParameter="{Binding SomeValue}" Height="25" Name="ButtonCancel" Width="75" />

With the default command parameter, we can only assign one value as a command parameter. Supposed that we want to assign more than one value to the command, a multi binding command parameter.

First, we're gonna need a converter for the multibinding. Assuming that our multi value is all string type. We're going to put it in a namespace called 'Converter'

We won't need to convert it back, but the 'IMultiValueConverter' won't let us depricated the 'ConvertBack' function so let's just set the ConvertBack function with 'NotSupportedException'.

	Namespace Converter

	    Public Class MultiValueConverter
	        Implements IMultiValueConverter

	        ''' <summary>
	        ''' converter for multivalue strings, return list of passed parameters
	        ''' </summary>
	        Public Function Convert(ByVal values() As Object, ByVal targetType As System.Type, ByVal parameter As Object, ByVal culture As System.Globalization.CultureInfo) As Object Implements System.Windows.Data.IMultiValueConverter.Convert
	            Dim tempList As New List(Of String)

	            If values IsNot Nothing Then
	                For Each tempValue As Object In values
	                    If TypeOf tempValue Is String Then
	                        tempList.Add(CType(tempValue, String))
	                    End If
	                Next
	            End If
	            
	            Return tempList
	        End Function

	        ''' <summary>
	        ''' Default function from interface, not used
	        ''' </summary>
	        Public Function ConvertBack(ByVal value As Object, ByVal targetTypes() As System.Type, ByVal parameter As Object, ByVal culture As System.Globalization.CultureInfo) As Object() Implements System.Windows.Data.IMultiValueConverter.ConvertBack
	            Throw New NotSupportedException("Cannot convert back")
	        End Function
	    End Class

	End Namespace

Put the 'Converter' namespace into the xaml file

	xmlns:converter="clr-namespace:Converter"

And we'll put our multivalue converter as a windows resource

	<Window.Resources>

        <!-- converter -->
        <converter:MultiValueConverter x:Key="myMultiValueConverter"/>

    </Window.Resources>

Let's get back to our previous button, we're going to implement our multi binding

	<Button Content="Close" Command="{Binding Path=CloseCommand}" CommandParameter="{Binding SomeValue}" Height="25" Name="ButtonCancel" Width="75">
		<Button.CommandParameter>
			<MultiBinding Converter="{StaticResource myMultiValueConverter}">
                <Binding Path="SomeValue" />
                <Binding Path="SomeOtherValue" />
            </MultiBinding>
		</Button.CommandParameter>
	</Button>

On the backend function, the binded values will passed as list of string




