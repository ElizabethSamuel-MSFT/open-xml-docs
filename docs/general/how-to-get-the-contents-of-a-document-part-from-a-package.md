---

api_name:
- Microsoft.Office.DocumentFormat.OpenXML.Packaging
api_type:
- schema
ms.assetid: b0d3d890-431a-4838-89dc-1f0dccd5dcd0
title: 'How to: Get the contents of a document part from a package'
ms.suite: office

ms.author: o365devx
author: o365devx
ms.topic: conceptual
ms.date: 01/08/2025
ms.localizationpriority: high
---
# Get the contents of a document part from a package

This topic shows how to use the classes in the Open XML SDK for
Office to retrieve the contents of a document part in a Wordprocessing
document programmatically.



--------------------------------------------------------------------------------
[!include[Structure](../includes/word/packages-and-document-parts.md)]


---------------------------------------------------------------------------------
## Getting a WordprocessingDocument Object

The code starts with opening a package file by passing a file name to
one of the overloaded <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument.Open*> methods (Visual Basic .NET Shared
method or C\# static method) of the <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument> class that takes a
string and a Boolean value that specifies whether the file should be
opened in read/write mode or not. In this case, the Boolean value is
`false` specifying that the file should be
opened in read-only mode to avoid accidental changes.

### [C#](#tab/cs-1)
[!code-csharp[](../../samples/word/get_the_contents_of_a_part_from_a_package/cs/Program.cs#snippet1)]

### [Visual Basic](#tab/vb-1)
[!code-vb[](../../samples/word/get_the_contents_of_a_part_from_a_package/vb/Program.vb#snippet1)]
***

[!include[Using Statement](../includes/word/using-statement.md)]


---------------------------------------------------------------------------------

[!include[Structure](../includes/word/structure.md)]

--------------------------------------------------------------------------------
## Comments Element

In this how-to, you are going to work with comments. Therefore, it is
useful to familiarize yourself with the structure of the `<comments/>` element. The following information
from the [!include[ISO/IEC 29500 URL](../includes/iso-iec-29500-link.md)]
specification can be useful when working with this element.

This element specifies all of the comments defined in the current
document. It is the root element of the comments part of a
WordprocessingML document.Consider the following WordprocessingML
fragment for the content of a comments part in a WordprocessingML
document:

```xml
    <w:comments>
      <w:comment … >
        …
      </w:comment>
    </w:comments>
```

The **comments** element contains the single
comment specified by this document in this example.

&copy; [!include[ISO/IEC 29500 version](../includes/iso-iec-29500-version.md)]

The following XML schema fragment defines the contents of this element.

```xml
    <complexType name="CT_Comments">
       <sequence>
           <element name="comment" type="CT_Comment" minOccurs="0" maxOccurs="unbounded"/>
       </sequence>
    </complexType>
```

--------------------------------------------------------------------------------
## How the Sample Code Works

After you have opened the source file for reading, you create a `mainPart` object by instantiating the `MainDocumentPart`. Then you can create a reference
to the `WordprocessingCommentsPart` part of
the document.

### [C#](#tab/cs-2)
[!code-csharp[](../../samples/word/get_the_contents_of_a_part_from_a_package/cs/Program.cs#snippet2)]

### [Visual Basic](#tab/vb-2)
[!code-vb[](../../samples/word/get_the_contents_of_a_part_from_a_package/vb/Program.vb#snippet2)]
***


You can then use a `StreamReader` object to
read the contents of the `WordprocessingCommentsPart` part of the document
and return its contents.

### [C#](#tab/cs-3)
[!code-csharp[](../../samples/word/get_the_contents_of_a_part_from_a_package/cs/Program.cs#snippet3)]

### [Visual Basic](#tab/vb-3)
[!code-vb[](../../samples/word/get_the_contents_of_a_part_from_a_package/vb/Program.vb#snippet3)]
***


--------------------------------------------------------------------------------
## Sample Code
The following code retrieves the contents of a `WordprocessingCommentsPart` part contained in a
`WordProcessing` document package. You can
run the program by calling the `GetCommentsFromDocument` method as shown in the
following example.

### [C#](#tab/cs-4)
[!code-csharp[](../../samples/word/get_the_contents_of_a_part_from_a_package/cs/Program.cs#snippet4)]

### [Visual Basic](#tab/vb-4)
[!code-vb[](../../samples/word/get_the_contents_of_a_part_from_a_package/vb/Program.vb#snippet4)]
***

Following is the complete code example in both C\# and Visual Basic.

### [C#](#tab/cs)
[!code-csharp[](../../samples/word/get_the_contents_of_a_part_from_a_package/cs/Program.cs#snippet0)]

### [Visual Basic](#tab/vb)
[!code-vb[](../../samples/word/get_the_contents_of_a_part_from_a_package/vb/Program.vb#snippet0)]
***

--------------------------------------------------------------------------------
## See also


[Open XML SDK class library
reference](/office/open-xml/open-xml-sdk)
