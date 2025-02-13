---

api_name:
- Microsoft.Office.DocumentFormat.OpenXML.Packaging
api_type:
- schema
ms.assetid: 03636fa2-be44-4e8d-9c26-7d38415bb459
title: Structure of a WordprocessingML document
ms.suite: office

ms.author: o365devx
author: o365devx
ms.topic: conceptual
ms.date: 01/12/2024
ms.localizationpriority: high
---
# Structure of a WordprocessingML document

This topic discusses the basic structure of a **WordprocessingML** document and reviews important
Open XML SDK classes that are used most often to create **WordprocessingML** documents.

The basic document structure of a **WordProcessingML** document consists of the `<document>` and `<body>` elements, followed by one or more block
level elements such as `<p>`, which
represents a paragraph. A paragraph contains one or more `<r>` elements. The `<r>` stands for run, which is a region of text
with a common set of properties, such as formatting. A run contains one
or more `<t>` elements. The `<t>` element contains a range of text.


## Important WordprocessingML Parts

The Open XML SDK API provides strongly-typed classes in the
DocumentFormat.OpenXML.WordprocessingML namespace that correspond to
**WordprocessingML** elements.

The following table lists some important **WordprocessingML** elements, the **WordprocessingML** document package part that the
element corresponds to (where applicable) and the managed class that
represents the element in the Open XML SDK API.

| **Package Part** | **WordprocessingML Element** | **Open XML SDK Class** | **Description** |
|---|---|---|---|
| Main Document|document | <xref:DocumentFormat.OpenXml.Wordprocessing.Document> | The root element for the main document part. |
| Comments | comments | <xref:DocumentFormat.OpenXml.Wordprocessing.Comments> | The root element for the comments part. |
| Document Settings | settings | <xref:DocumentFormat.OpenXml.Wordprocessing.Settings> | The root element for the document settings part. |
| Endnotes | endnotes | <xref:DocumentFormat.OpenXml.Wordprocessing.Endnotes> | The root element for the endnotes part. |
| Footer | ftr | <xref:DocumentFormat.OpenXml.Wordprocessing.Footer> | The root element for the footer part. |
| Footnotes | footnotes | <xref:DocumentFormat.OpenXml.Wordprocessing.Footnotes> | The root element for the footnotes part. |
| Glossary Document | glossaryDocument | <xref:DocumentFormat.OpenXml.Wordprocessing.GlossaryDocument> | The root element for the glossary document part. |
| Header | hdr | <xref:DocumentFormat.OpenXml.Wordprocessing.Header> | The root element for the header part. |
| Style Definitions | styles | <xref:DocumentFormat.OpenXml.Wordprocessing.Styles> | The root element for a Style Definitions part. |


## Minimum Document Scenario

A **WordprocessingML** document is organized
around the concept of stories. A story is a region of content in a **WordprocessingML** document. **WordprocessingML** stories include:

-   comment

-   endnote

-   footer

-   footnote

-   frame, glossary document

-   header

-   main story

-   subdocument

-   text box

Not all stories must be present in a valid **WordprocessingML** document. The simplest, valid
**WordprocessingML** document only requires a
single story—the main document story. In **WordprocessingML**, the main document story is
represented by the main document part. At a minimum, to create a valid
**WordprocessingML** document using code, add a
main document part to the document.

The following information from the [!include[ISO/IEC 29500 URL](../includes/iso-iec-29500-link.md)]
introduces the WordprocessingML elements required in the main document
part in order to complete the minimum document scenario.

The main document story of the simplest WordprocessingML document
consists of the following XML elements:

- `document` — The root element for a WordprocessingML's main document part,
which defines the main document story.

- `body` — The container for the collection of block-level structures that
comprise the main story.

- `p` — A paragraph.

- `r` — A run.

- `t` — A range of text.

&copy; [!include[ISO/IEC 29500 version](../includes/iso-iec-29500-version.md)]

### Open XML SDK Code Example

The following code uses the Open XML SDK to create a simple **WordprocessingML** document that contains the text passed in as the second parameter

### [C#](#tab/cs)
[!code-csharp[](../../samples/word/structure_of_a_wordprocessingml/cs/Program.cs#snippet0)]

### [Visual Basic](#tab/vb)
[!code-vb[](../../samples/word/structure_of_a_wordprocessingml/vb/Program.vb#snippet0)]
***

### Generated WordprocessingML

After you run the Open XML SDK code in the previous section to
generate a document, you can explore the contents of the .zip package to
view the **WordprocessingML** XML code. To view
the .zip package, rename the extension on the minimum document from
.docx to .zip. The .zip package contains the parts that make up the
document. In this case, since the code created a minimal **WordprocessingML** document, there is only a single
part—the main document part.The following figure shows the structure
under the word folder of the .zip package for a minimum document that
contains a single line of text.**Art
placeholder**The document.xml file corresponds to the **WordprocessingML** main document part and it is
this part that contains the content of the main body of the document.
The following XML code is generated in the document.xml file when you
run the Open XML SDK code in the previous section.

```xml
<?xml version="1.0" encoding="utf-8"?>
<w:document xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">
  <w:body>
    <w:p>
      <w:r>
        <w:t>The text passed as the second parameter goes here</w:t>
      </w:r>
    </w:p>
  </w:body>
</w:document>
```

## Typical Document Scenario

A typical document will not be a blank, minimum document. A typical
document might contain comments, headers, footers, footnotes, and
endnotes, for example. Each of these additional parts is contained
within the zip package of the wordprocessing document.

The following figure shows many of the parts that you would find in a
typical document.

Figure 1. Typical document structure

  
 ![Structure of a WordprocessingML Document](../media/odc_oxml_wd_documentstructure_fig01.jpg)
