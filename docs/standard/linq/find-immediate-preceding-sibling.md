---
title: Comment trouver le LINQ to XML frère précédent
description: 'Découvrez comment trouver le frère qui précède immédiatement un nœud. Deux méthodes sont affichées : l’une utilise XPathEvaluate, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 9be39c20a99920482899efa934003957ffc696b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545614"
---
# <a name="how-to-find-the-immediate-preceding-sibling-linq-to-xml"></a><span data-ttu-id="318da-104">Comment rechercher le frère précédent (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="318da-104">How to find the immediate preceding sibling (LINQ to XML)</span></span>

<span data-ttu-id="318da-105">Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> pour rechercher le frère qui précède immédiatement un nœud, et comment utiliser LINQ to XML requête pour faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="318da-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the sibling that immediately precedes a node, and how to use LINQ to XML query to do the same thing.</span></span> <span data-ttu-id="318da-106">En raison de la différence de sémantique des prédicats positionnels pour les axes frères précédents dans XPath par opposition à LINQ to XML, il s’agit de l’une des comparaisons les plus intéressantes.</span><span class="sxs-lookup"><span data-stu-id="318da-106">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to LINQ to XML, this is one of the more interesting comparisons.</span></span>

## <a name="example-find-the-next-to-last-element"></a><span data-ttu-id="318da-107">Exemple : Rechercher le en regard du dernier élément</span><span class="sxs-lookup"><span data-stu-id="318da-107">Example: Find the next to last element</span></span>

<span data-ttu-id="318da-108">Dans cet exemple, la requête LINQ to XML utilise l' <xref:System.Linq.Enumerable.Last%2A> opérateur pour rechercher le dernier nœud dans la collection retournée par <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="318da-108">In this example, the LINQ to XML query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="318da-109">Par contraste, l’expression XPath utilise un prédicat avec une valeur de 1 pour rechercher l’élément précédent.</span><span class="sxs-lookup"><span data-stu-id="318da-109">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

```csharp
XElement root = XElement.Parse(
    @"<Root>
    <Child1/>
    <Child2/>
    <Child3/>
    <Child4/>
</Root>");
XElement child4 = root.Element("Child4");

// LINQ to XML query
XElement el1 =
    child4
    .ElementsBeforeSelf()
    .Last();

// XPath expression
XElement el2 =
    ((IEnumerable)child4
                 .XPathEvaluate("preceding-sibling::*[1]"))
                 .Cast<XElement>()
                 .First();

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1/>
        <Child2/>
        <Child3/>
        <Child4/>
    </Root>
Dim child4 As XElement = root.Element("Child4")

' LINQ to XML query
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()

' XPath expression
Dim el2 As XElement = _
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _
    IEnumerable).Cast(Of XElement)().First()

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

<span data-ttu-id="318da-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="318da-110">This example produces the following output:</span></span>

```output
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="318da-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="318da-111">See also</span></span>

- [<span data-ttu-id="318da-112">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="318da-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
