---
title: Comment rechercher des descendants d’un élément enfant-LINQ to XML
description: 'Découvrez comment rechercher des descendants d’un élément enfant ou une séquence d’éléments enfants. Deux méthodes sont affichées : l’une utilise XPathEvaluate, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: 675fb7da42f874e21374a6fbc4b61ae90a78caf2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552356"
---
# <a name="how-to-find-descendants-of-a-child-element-linq-to-xml"></a><span data-ttu-id="afc33-104">Comment rechercher des descendants d’un élément enfant (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="afc33-104">How to find descendants of a child element (LINQ to XML)</span></span>

<span data-ttu-id="afc33-105">Cet article montre comment utiliser <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> pour rechercher les éléments descendants d’une séquence d’éléments enfants, et comment utiliser LINQ to XML requête pour rechercher les mêmes éléments.</span><span class="sxs-lookup"><span data-stu-id="afc33-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the descendant elements of a sequence of child elements, and how to use LINQ to XML query to find the same elements.</span></span>

## <a name="example-find-all-the-text-descendant-elements-of-all-the-paragraph-elements"></a><span data-ttu-id="afc33-106">Exemple : Rechercher tous les `Text` éléments descendants de tous les `Paragraph` éléments</span><span class="sxs-lookup"><span data-stu-id="afc33-106">Example: Find all the `Text` descendant elements of all the `Paragraph` elements</span></span>

<span data-ttu-id="afc33-107">Cet exemple extrait du texte à partir d’une représentation XML d’un document de traitement de texte simple.</span><span class="sxs-lookup"><span data-stu-id="afc33-107">This example extracts text from an XML representation of a simple word processing document.</span></span> <span data-ttu-id="afc33-108">Elle sélectionne tout d’abord tous les `Paragraph` éléments, en ignorant l' `Comment` élément, puis sélectionne tous les `Text` éléments descendants de chaque `Paragraph` élément.</span><span class="sxs-lookup"><span data-stu-id="afc33-108">It first selects all `Paragraph` elements, ignoring the `Comment` element, and then it selects all the `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="afc33-109">Il effectue cette tâche de deux manières : avec <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> et avec LINQ to XML requête.</span><span class="sxs-lookup"><span data-stu-id="afc33-109">It does this task in two ways: with <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> and with LINQ to XML query.</span></span> <span data-ttu-id="afc33-110">Il compare ensuite les résultats et les trouve identiques.</span><span class="sxs-lookup"><span data-stu-id="afc33-110">It then compares the results and finds them identical.</span></span>

<span data-ttu-id="afc33-111">L’expression XPath est  `./Paragraph//Text/text()` .</span><span class="sxs-lookup"><span data-stu-id="afc33-111">The XPath expression is  `./Paragraph//Text/text()`.</span></span>

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

<span data-ttu-id="afc33-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="afc33-112">This example produces the following output:</span></span>

```output
Results are identical
This is the start of a sentence.  This is the second sentence.
```

## <a name="see-also"></a><span data-ttu-id="afc33-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afc33-113">See also</span></span>

- [<span data-ttu-id="afc33-114">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afc33-114">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
