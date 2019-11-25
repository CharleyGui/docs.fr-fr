---
title: Littéral d'élément XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347025"
---
# <a name="xml-element-literal-visual-basic"></a>Littéral d'élément XML (Visual Basic)

A literal that represents an <xref:System.Xml.Linq.XElement> object.

## <a name="syntax"></a>Syntaxe

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Composants

- `<`

  Requis. Opens the starting element tag.

- `name`

  Requis. Nom de l'élément. The format is one of the following:

  - Literal text for the element name, of the form `[ePrefix:]eName`, where:

    |Élément|Description|
    |---|---|
    |`ePrefix`|Optionnel. XML namespace prefix for the element. Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.|
    |`eName`|Requis. Nom de l'élément. The format is one of the following:<br /><br /> - Literal text. See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />- Embedded expression of the form `<%= eNameExp %>`. The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.|

  - Embedded expression of the form `<%= nameExp %>`. The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>. An embedded expression is not allowed in a closing tag of an element.

- `attributeList`

  Optionnel. List of attributes declared in the literal.

  `attribute [ attribute ... ]`

  Each `attribute` has one of the following syntaxes:

  - Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:

    |Élément|Description|
    |---|---|
    |`aPrefix`|Optionnel. XML namespace prefix for the attribute. Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.|
    |`aName`|Requis. Nom de l'attribut. The format is one of the following:<br /><br /> - Literal text. See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />- Embedded expression of the form `<%= aNameExp %>`. The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.|
    |`aValue`|Optionnel. Value of the attribute. The format is one of the following:<br /><br /> - Literal text, enclosed in quotation marks.<br />- Embedded expression of the form `<%= aValueExp %>`. Any type is allowed.|

  - Embedded expression of the form `<%= aExp %>`.

- `/>`

  Optionnel. Indicates that the element is an empty element, without content.

- `>`

  Requis. Ends the beginning or empty element tag.

- `elementContents`

  Optionnel. Content of the element.

  `content [ content ... ]`

  Each `content` can be one of the following:

  - Literal text. All the white space in `elementContents` becomes significant if there is any literal text.

  - Embedded expression of the form `<%= contentExp %>`.

  - XML element literal.

  - XML comment literal. See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).

  - XML processing instruction literal. See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).

  - XML CDATA literal. See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).

- `</[name]>`

  Optionnel. Represents the closing tag for the element. The optional `name` parameter is not allowed when it is the result of an embedded expression.

## <a name="return-value"></a>Valeur de retour

Objet <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Notes

You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.

> [!NOTE]
> An XML literal can span multiple lines without using line continuation characters. This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.

Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal. For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).

The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.

## <a name="xml-namespaces"></a>Espaces de noms XML

XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code. You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax. For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes. However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression. The embedded expression can access only the global XML namespace.

The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code. Global XML namespaces that are not used do not appear in the generated code.

## <a name="example"></a>Exemple

The following example shows how to create a simple XML element that has two nested empty elements.

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

The example displays the following text. Notice that the literal preserves the structure of the empty elements.

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a>Exemple

The following example shows how to use embedded expressions to name an element and create attributes.

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

Ce code affiche le texte suivant :

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a>Exemple

L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. It then uses the prefix of the namespace to create an XML literal and displays the element's final form.

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

Ce code affiche le texte suivant :

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace. The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element. However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Littéraux de commentaires XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Littéral CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports (instruction) (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
