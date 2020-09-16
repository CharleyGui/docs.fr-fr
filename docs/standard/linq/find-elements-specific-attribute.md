---
title: Comment rechercher des éléments avec un LINQ to XML d’attributs spécifique
description: 'Découvrez comment rechercher tous les éléments qui ont un attribut spécifique (quelle que soit la valeur). Deux méthodes sont affichées : l’une utilise XPathEvaluate, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: 2a747e7609e2b130249a7635d8448577d035f939
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545648"
---
# <a name="how-to-find-elements-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="7eb7b-104">Comment rechercher des éléments avec un attribut spécifique (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7eb7b-104">How to find elements with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="7eb7b-105">Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> pour rechercher tous les éléments qui ont un attribut spécifique (quelle que soit la valeur), et comment utiliser LINQ to XML requête pour faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="7eb7b-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find all elements that have a specific attribute (regardless of value), and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-all-elements-that-have-the-select-attribute"></a><span data-ttu-id="7eb7b-106">Exemple : Rechercher tous les éléments qui ont l' `Select` attribut</span><span class="sxs-lookup"><span data-stu-id="7eb7b-106">Example: Find all elements that have the `Select` attribute</span></span>

<span data-ttu-id="7eb7b-107">L’exemple suivant crée une arborescence XML, puis recherche les éléments qui ont l' `Select` attribut.</span><span class="sxs-lookup"><span data-stu-id="7eb7b-107">The following example creates an XML tree and then finds the elements that have the `Select` attribute.</span></span>

<span data-ttu-id="7eb7b-108">L'expression XPath est `./*[@Select]`.</span><span class="sxs-lookup"><span data-stu-id="7eb7b-108">The XPath expression is `./*[@Select]`.</span></span>

```csharp
XElement doc = XElement.Parse(
@"<Root>
    <Child1>1</Child1>
    <Child2 Select='true'>2</Child2>
    <Child3>3</Child3>
    <Child4 Select='true'>4</Child4>
    <Child5>5</Child5>
</Root>");

// LINQ to XML query
IEnumerable<XElement> list1 =
    from el in doc.Elements()
    where el.Attribute("Select") != null
    select el;

// XPath expression
IEnumerable<XElement> list2 =
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim doc As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child2 Select='true'>2</Child2>
        <Child3>3</Child3>
        <Child4 Select='true'>4</Child4>
        <Child5>5</Child5>
    </Root>

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    From el In doc.Elements() _
    Where el.@Select <> Nothing _
    Select el

' XPath expression
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()

If list1.Count() = list2.Count() And _
    list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="7eb7b-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7eb7b-109">This example produces the following output:</span></span>

```output
Results are identical
<Child2 Select="true">2</Child2>
<Child4 Select="true">4</Child4>
```

## <a name="see-also"></a><span data-ttu-id="7eb7b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eb7b-110">See also</span></span>

- [<span data-ttu-id="7eb7b-111">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7eb7b-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
