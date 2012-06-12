---
layout: post
title: "WPF VB.Net Save File Dialog"
description: ""
category: VB.Net
tags: [.Net, WPF, MVVM]
---
{% include JB/setup %}

##The Idea

Saving content to a txt file

1. A button on a XAML File
2. Upon clicked, open a save file dialog
3. Choose a file or create new file
4. File created if not exists, data written to file

##The Chunks

1. We're going to create a SaveFileDialog class from .Net to open a save file dialog

		' Create an instance of the open file dialog box.
    	Dim exportFileDialog As New SaveFileDialog

2. Only `.txt` files allowed, we're putting a restriction by using `filter`

	   ' Set filter options and filter index.
        exportFileDialog.Filter = "Text Files (*.txt)|*.txt"

3. Set the 'open file' window title and show it to user

		exportFileDialog.Title = "Save as Text file"
        exportFileDialog.ShowDialog()

4. Check if user input valid file name

	If exportFileDialog.FileName <> "" Then

5. Get filename from user input

	Dim selectedfile As String = exportFileDialog.FileName

6. Check if file exists, if not, create file

	If System.IO.File.Exists(selectedfile) <> True Then
        System.IO.File.Create(selectedfile).Dispose()
    End If

7. We're using `StreamWriter` to write to file, don't forget to close the stream after use

	 Dim objWriter As New System.IO.StreamWriter(selectedfile)
     objWriter.Write("Writing to file!!")
     objWriter.Close()

##The Final Function Code

		Private Function SaveToTextFile() As Boolean
            ' Create an instance of the open file dialog box.
            Dim exportFileDialog As New SaveFileDialog
 
            ' Set filter options and filter index.
            exportFileDialog.Filter = "Text Files (*.txt)|*.txt"
            exportFileDialog.Title = "Save as Text file"
            exportFileDialog.ShowDialog()
 
            ' Call the ShowDialog method to show the dialogbox.
            If exportFileDialog.FileName <> "" Then
                Dim selectedfile As String = exportFileDialog.FileName
 
                If System.IO.File.Exists(selectedfile) <> True Then
                    System.IO.File.Create(selectedfile).Dispose()
                End If
 
                Dim objWriter As New System.IO.StreamWriter(selectedfile)
                objWriter.Write("Writing to file!!")
                
                objWriter.Close()
                MsgBox("Text written to file")
 
            End If
 
            Return True
        End Function
