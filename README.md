<div align="center">

## GetResource


</div>

### Description

Reads embeded files from your executable programs (such as xml, images, etc.) Allows you to distribute one program - the exe, but still access your data and images needed with the program.
 
### More Info
 
This only allows you to read the data, not update/delete/add to it, except during design time.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Lewis E\. Moten III](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/lewis-e-moten-iii.md)
**Level**          |Beginner
**User Rating**    |4.7 (14 globes from 3 users)
**Compatibility**  |VB\.NET
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__10-2.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/lewis-e-moten-iii-getresource__10-954/archive/master.zip)





### Source Code

```
Public Function GetResource(ByVal filename As String) As System.IO.Stream
    ' Demo Instructions:
    '
    ' Add an XML document to your project called "test.xml"
    '
    ' Click the file and under properties, set BuildAction to "Embedded Resource"
    '
    ' paste this routine in one of your classes or forms.
    '
    ' Add the import to the top of your class
    ' Imports System.Xml.XmlDocument
    '
    ' Dim the XML Document object
    ' Dim xmldoc As XmlDocument = New XmlDocument()
    '
    ' Load the XML document from the resource
    ' xmldoc.Load(GetResource("test.xml"))
    '
    ' Congratulations. You have learned how to embed files within
    ' your program and read them at run-time
    '
    Dim oAssembly As Reflection.Assembly = MyClass.GetType.Assembly
    Dim sFiles() As String
    Dim sFile As String
    ' prefix filename with namespace
    filename = oAssembly.GetName.Name & "." & filename
    ' get a list of all embeded files
    sFiles = oAssembly.GetManifestResourceNames()
    ' loop through each file
    For Each sFile In sFiles
      ' found the file? return the stream
      If sFile = filename Then
        Return oAssembly.GetManifestResourceStream(sFile)
      End If
    Next
  End Function
```

