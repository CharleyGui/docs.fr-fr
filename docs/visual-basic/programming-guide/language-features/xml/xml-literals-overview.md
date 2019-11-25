---
title: Vue d'ensemble des littéraux XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e5d2465d145f4059600121c6cef30bb2c74a8c1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346199"
---
# <a name="xml-literals-overview-visual-basic"></a>Vue d'ensemble des littéraux XML (Visual Basic)
An *XML literal* allows you to incorporate XML directly into your Visual Basic code. The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is the similar to the XML 1.0 syntax. This makes it easier to create XML elements and documents programmatically because your code has the same structure as the final XML.  
  
 Visual Basic compiles XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides a simple object model for creating and manipulating XML, and this model integrates well with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.  
  
 You can embed a Visual Basic expression in an XML literal. At run time, your application creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for each literal, incorporating the values of the embedded expressions. This lets you specify dynamic content inside an XML literal. For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 For more information about the differences between the XML literal syntax and the XML 1.0 syntax, see [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Simple Literals  
 You can create a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object in your Visual Basic code by typing or pasting in valid XML. An XML element literal returns an <xref:System.Xml.Linq.XElement> object. For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). The following example creates an XML element that has several child elements.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 You can create an XML document by starting an XML literal with `<?xml version="1.0"?>`, as shown in the following example. An XML document literal returns an <xref:System.Xml.Linq.XDocument> object. For more information, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> The XML literal syntax in Visual Basic is not identical to the syntax in the XML 1.0 specification. For more information, see [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Line Continuation  
 An XML literal can span multiple lines without using line continuation characters (the space-underscore-enter sequence). This makes it easier to compare XML literals in code with XML documents.  
  
 The compiler treats line continuation characters as part of an XML literal. Therefore, you should use the space-underscore-enter sequence only when it belongs in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.  
  
 However, you do need line continuation characters if you have a multiline expression in an embedded expression. For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Embedding Queries in XML Literals  
 You can use a query in an embedded expression. When you do this, the elements returned by the query are added to the XML element. This lets you add dynamic content, such as the result of a user's query, to an XML literal.  
  
 For example, the following code uses an embedded query to create XML elements from the members of the `phoneNumbers2` array and then add those elements as children of `contact2`.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>How the Compiler Creates Objects from XML Literals  
 The Visual Basic compiler translates XML literals into calls to the equivalent [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] constructors to build up the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object. For example, the Visual Basic compiler will translate the following code example into a call to the <xref:System.Xml.Linq.XProcessingInstruction> constructor for the XML version instruction, calls to the <xref:System.Xml.Linq.XElement> constructor for the `<contact>`, `<name>`, and `<phone>` elements, and calls to the <xref:System.Xml.Linq.XAttribute> constructor for the `type` attribute. Specifically, given the attributes in the following sample, the Visual Basic compiler will call the <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> constructor twice. The first will pass the value `type` for the `name` parameter and the value `home` for the `value` parameter. The second will also pass the value `type` for the `name` parameter, but the value `work` for the `value` parameter.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md)
