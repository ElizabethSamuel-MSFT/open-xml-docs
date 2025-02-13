---

api_name:
- Microsoft.Office.DocumentFormat.OpenXML.Packaging
api_type:
- schema
ms.assetid: 1771fc05-dd94-40e3-a788-6a13809d64f3
title: 'Create a word processing document by providing a file name'
ms.suite: office

ms.author: o365devx
author: o365devx
ms.topic: conceptual
ms.date: 05/13/2024
ms.localizationpriority: high
---
# Create a word processing document by providing a file name

This topic shows how to use the classes in the Open XML SDK for
Office to programmatically create a word processing document.



--------------------------------------------------------------------------------
## Creating a WordprocessingDocument Object

In the Open XML SDK, the <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument> class represents a
Word document package. To create a Word document, you create an instance
of the <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument> class and
populate it with parts. At a minimum, the document must have a main
document part that serves as a container for the main text of the
document. The text is represented in the package as XML using
WordprocessingML markup.

To create the class instance you call the <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument.Create(System.String,DocumentFormat.OpenXml.WordprocessingDocumentType)> 
method. Several <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument.Create%2A> methods are provided, each with a
different signature. The sample code in this topic uses the `Create` method with a signature that requires two
parameters. The first parameter takes a full path string that represents
the document that you want to create. The second parameter is a member
of the <xref:DocumentFormat.OpenXml.WordprocessingDocumentType> enumeration.
This parameter represents the type of document. For example, there is a
different member of the `WordProcessingDocumentType` enumeration for each
of document, template, and the macro enabled variety of document and
template.

> [!NOTE]
> Carefully select the appropriate `WordProcessingDocumentType` and verify that the persisted file has the correct, matching file extension. If the `WordProcessingDocumentType` does not match the file extension, an error occurs when you open the file in Microsoft Word.



The code that calls the `Create` method is
part of a `using` statement followed by a
bracketed block, as shown in the following code example.

### [C#](#tab/cs-0)
[!code-csharp[](../../samples/word/create_by_providing_a_file_name/cs/Program.cs#snippet1)]
### [Visual Basic](#tab/vb-0)
[!code-vb[](../../samples/word/create_by_providing_a_file_name/vb/Program.vb#snippet1)]
***

[!include[Using Statement](../includes/word/using-statement.md)]

Once you have created the Word document package, you can add parts to
it. To add the main document part you call the <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument.AddMainDocumentPart%2A> method of the <xref:DocumentFormat.OpenXml.Packaging.WordprocessingDocument> class. Having done that,
you can set about adding the document structure and text.


--------------------------------------------------------------------------------

[!include[Structure](../includes/word/structure.md)]

--------------------------------------------------------------------------------
## Generating the WordprocessingML Markup

To create the basic document structure using the Open XML SDK, you
instantiate the `Document` class, assign it
to the `Document` property of the main
document part, and then add instances of the `Body`, `Paragraph`,
`Run` and `Text`
classes. This is shown in the sample code listing, and does the work of
generating the required WordprocessingML markup. While the code in the
sample listing calls the `AppendChild` method
of each class, you can sometimes make code shorter and easier to read by
using the technique shown in the following code example.

### [C#](#tab/cs-1)
```csharp
    mainPart.Document = new Document(
       new Body(
          new Paragraph(
             new Run(
                new Text("Create text in body - CreateWordprocessingDocument")))));
```

### [Visual Basic](#tab/vb-1)
```vb
    mainPart.Document = New Document(New Body(New Paragraph(New Run(New Text("Create text in body - CreateWordprocessingDocument")))))
```
***


--------------------------------------------------------------------------------
## Sample Code
The `CreateWordprocessingDocument` method can
be used to create a basic Word document. You call it by passing a full
path as the only parameter. The following code example creates the
Invoice.docx file in the Public Documents folder.

### [C#](#tab/cs-2)
[!code-csharp[](../../samples/word/create_by_providing_a_file_name/cs/Program.cs#snippet2)]
### [Visual Basic](#tab/vb-2)
[!code-vb[](../../samples/word/create_by_providing_a_file_name/vb/Program.vb#snippet2)]
***


The file extension, .docx, matches the type of file specified by the
**WordprocessingDocumentType.Document**
parameter in the call to the **Create** method.

Following is the complete code example in both C\# and Visual Basic.

### [C#](#tab/cs)
[!code-csharp[](../../samples/word/create_by_providing_a_file_name/cs/Program.cs#snippet0)]

### [Visual Basic](#tab/vb)
[!code-vb[](../../samples/word/create_by_providing_a_file_name/vb/Program.vb#snippet0)]
***

--------------------------------------------------------------------------------
## See also


- [Open XML SDK class library reference](/office/open-xml/open-xml-sdk)
