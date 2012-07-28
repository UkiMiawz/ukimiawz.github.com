---
layout: post
title: "XAML Binding Enumerations"
description: "Binding an enumerations in XAML"
category: VB.Net
tags: [.Net, WPF, MVVM]
---
{% include JB/setup %}

Supposed that we have these 'enumerations'

	Namespace AnimalsEnumerations

		''' <summary>
	    ''' Type of animal
	    ''' </summary>
	    Public Enum Animals
	        Cat
	        Cow
	        Monkey
	    End Enum

	End Namespace

And we want to bind it to a combobox. We have this combobox

	<ComboBox Height="23" Width="auto" x:Name="cboDataBits" />

Now we want to bind the animals enumerations into the combo box. The idea is to put it into windows resource and bind it to the combobox as a static resource.

First of all, let's give the enumerations a namespace, supposed we call it 'Animals'

Then, we have to include the enumerations class namespace 

	xmlns:softcore="clr-namespace:AnimalEnumerations;assembly=AnimalsProject"

Put the window resources tag

	<Window.Resources>
	</Window.Resources>

Put the enumerations inside as 'ObjectDataProvider'

	<Window.Resources>

    	    <!-- animal type -->
        	<ObjectDataProvider x:Key="animalDS" 
        	d:IsDataSource="True" MethodName="GetSortedEnumNames" 
        	ObjectType="{x:Type utility:GetEnumValues}">
            	<ObjectDataProvider.MethodParameters>
                	<x:Type TypeName="softcore:AnimalsEnumerations"/>
            	</ObjectDataProvider.MethodParameters>
        	</ObjectDataProvider>

	</Window.Resources>

You might realized that there are some weird functions we're calling there, GetSortedEnumNames and GetEnumValues. We will get it to get the enum values and sorted it before binding the values to the combo box

	Namespace Utility

		Public Class GetEnumValues

		        ''' <summary>
		        ''' Change enum to list of strings
		        ''' </summary>
		        Public Function GetSortedEnumNames(ByVal t As Type) As String()

		            'first do a sanity check, make sure the developer 
		            'is passing us an enum
		            If t.BaseType.FullName = "System.Enum" Then
		                Dim strOut() As String = [Enum].GetNames(t)
		                Array.Sort(strOut)
		                Return strOut
		            Else
		                Throw New ArgumentException("Must be an enum", "t")
		            End If
		        End Function

		        ''' <summary>
		        ''' Change enum to list of strings
		        ''' </summary>
		        Public Function GetSortedEnumValues(ByVal t As Type) As List(Of Integer)
		            Dim strOut As New List(Of Integer)
		            'first do a sanity check, make sure the developer 
		            'is passing us an enum
		            If t.BaseType.FullName = "System.Enum" Then
		                For Each i As Integer In [Enum].GetValues(t)
		                    strOut.Add(i)
		                Next
		                Return strOut
		            Else
		                Throw New ArgumentException("Must be an enum", "t")
		            End If
		        End Function

		        Public Sub New()

		        End Sub

		    End Class

End Namespace

Don't forgot to add the namespace to the XAML file

	xmlns:softcore="clr-namespace:Utility;assembly=AnimalsProject"                             

To use it on the combobox, we'll simply add it into the items source binding

	<ComboBox Height="23" Width="auto" x:Name="cboDataBits" 
		ItemsSource="{Binding Mode=OneWay, Source={StaticResource dataBitsDS}}" />
                            