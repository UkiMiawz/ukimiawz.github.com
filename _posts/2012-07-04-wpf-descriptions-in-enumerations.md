---
layout: post
title: "WPF Descriptions in enumerations"
description: "Implementing description in enumerations"
category: VB.Net
tags: [.Net, WPF, MVVM]
---
{% include JB/setup %}

Supposed that we have these 'enumerations'

	''' <summary>
    ''' Type of animal
    ''' </summary>
    Public Enum Animals
        Cat
        Cow
        Monkey
    End Enum

And we want to add some descriptions into the enumerations. For example, I want not just ordinary cat, but a spinning cat. Monkey is mainstream, but flying monkey, now we're talking!

We can just add the descriptions in the enumerations like this

	''' <summary>
    ''' Type of animal
    ''' </summary>
    Public Enum Animals
        <Description("Spinning Cat")> Cat
        <Description("Jumping Cow")> Cow
        <Description("Flying Monkey")> Monkey
    End Enum

And to read it, we will create a function to read the description in the tag.

'Credits : http://www.vbforums.com/showthread.php?t=550710'

This function will gets the <Description> attribute of an enum constant, if any. Otherwise it gets the string name of the enum member.


            Public Shared Function GetEnumDescription(ByVal EnumConstant As [Enum]) As String
                Dim fi As Reflection.FieldInfo = EnumConstant.GetType().GetField(EnumConstant.ToString())
                Dim aattr() As DescriptionAttribute = DirectCast(fi.GetCustomAttributes(GetType(DescriptionAttribute), False), DescriptionAttribute())
                If aattr.Length > 0 Then
                    Return aattr(0).Description
                Else
                    Return EnumConstant.ToString()
                End If
            End Function

Example usage given :

	Dim cat as string = GetEnumDescription(Animal.Cat)

Tada!