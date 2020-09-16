---
title: Comment rechercher des descendants d’un élément enfant-LINQ to XML
description: 'Découvrez comment rechercher des descendants d’un élément enfant ou une séquence d’éléments enfants. Deux méthodes sont affichées : l’une utilise XPathEvaluate, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: 2ac023ddc797f27f5f00eaf86ff6357096f333c8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559314"
---
# <a name="how-to-find-descendants-of-a-child-element-linq-to-xml"></a>Comment rechercher des descendants d’un élément enfant (LINQ to XML)

Cet article montre comment utiliser <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> pour rechercher les éléments descendants d’une séquence d’éléments enfants, et comment utiliser LINQ to XML requête pour rechercher les mêmes éléments.

## <a name="example-find-all-the-text-descendant-elements-of-all-the-paragraph-elements"></a>Exemple : Rechercher tous les `Text` éléments descendants de tous les `Paragraph` éléments

Cet exemple extrait du texte à partir d’une représentation XML d’un document de traitement de texte simple. Elle sélectionne tout d’abord tous les `Paragraph` éléments, en ignorant l' `Comment` élément, puis sélectionne tous les `Text` éléments descendants de chaque `Paragraph` élément. Il effectue cette tâche de deux manières : avec <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> et avec LINQ to XML requête. Il compare ensuite les résultats et les trouve identiques.

L’expression XPath est  `./Paragraph//Text/text()` .

```csharp
XElement root = XElement.Parse(
@"<Root>
  <Paragraph>
    <Text>This is the start of</Text>
  </Paragraph>
  <Comment>
    <Text>This comment isn't part of the paragraph text.</Text>
  </Comment>
  <Paragraph>
    <Annotation Emphasis='true'>
      <Text> a sentence.</Text>
    </Annotation>
  </Paragraph>
  <Paragraph>
    <Text>  This is the second sentence.</Text>
  </Paragraph>
</Root>");

// LINQ to XML query
string str1 =
    root
    .Elements("Paragraph")
    .Descendants("Text")
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

// XPath expression
string str2 =
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))
    .Cast<XText>()
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

if (str1 == str2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(str2);
```

```vb
Dim root As XElement = _
    <Root>
        <Paragraph>
            <Text>This is the start of</Text>
        </Paragraph>
        <Comment>
            <Text>This comment isn't part of the paragraph text.</Text>
        </Comment>
        <Paragraph>
            <Annotation Emphasis='true'>
                <Text> a sentence.</Text>
            </Annotation>
        </Paragraph>
        <Paragraph>
            <Text>This is the second sentence.</Text>
        </Paragraph>
    </Root>

' LINQ to XML query
Dim str1 As String = _
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _
    Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

' XPath expression
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _
    .Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

If str1 = str2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(str2)
```

Cet exemple produit la sortie suivante :

```output
Results are identical
This is the start of a sentence.  This is the second sentence.
```

## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (Visual Basic)](./comparison-xpath-linq-xml.md)
