---
title: Comment rechercher un seul descendant à l’aide de la méthode descendants-LINQ to XML
description: Utilisez la méthode d’axe XContainer. descendants pour rechercher un seul élément descendant portant un nom unique.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 9065309822bfb7c46da556fcf9b3a3b48df16302
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552541"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-linq-to-xml"></a><span data-ttu-id="c2e7e-103">Comment rechercher un seul descendant à l’aide de la méthode descendants (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c2e7e-103">How to find a single descendant using the Descendants method (LINQ to XML)</span></span>

<span data-ttu-id="c2e7e-104">Vous pouvez utiliser la <xref:System.Xml.Linq.XContainer.Descendants%2A> méthode AXIS pour rechercher un seul élément descendant nommé de façon unique.</span><span class="sxs-lookup"><span data-stu-id="c2e7e-104">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to find a single uniquely-named descendant element.</span></span> <span data-ttu-id="c2e7e-105">Cette technique est particulièrement utile lorsque vous souhaitez rechercher un descendant particulier avec un nom spécifique et peut être plus rapide et plus facile à utiliser que la navigation dans l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c2e7e-105">This technique is especially useful when you want to find a particular descendant with a specific name, and may be faster and easier to use than navigating the XML tree.</span></span>

## <a name="example-use-xcontainerdescendants-to-find-a-single-uniquely-named-descendant-element"></a><span data-ttu-id="c2e7e-106">Exemple : utiliser XContainer. descendants pour rechercher un seul élément descendant nommé de façon unique</span><span class="sxs-lookup"><span data-stu-id="c2e7e-106">Example: Use XContainer.Descendants to find a single uniquely-named descendant element</span></span>

<span data-ttu-id="c2e7e-107">Cet exemple utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2e7e-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <GrandChild1>GC1 Value</GrandChild1>
  </Child1>
  <Child2>
    <GrandChild2>GC2 Value</GrandChild2>
  </Child2>
  <Child3>
    <GrandChild3>GC3 Value</GrandChild3>
  </Child3>
  <Child4>
    <GrandChild4>GC4 Value</GrandChild4>
  </Child4>
</Root>");
string grandChild3 = (string)
    (from el in root.Descendants("GrandChild3")
    select el).First();
Console.WriteLine(grandChild3);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1>GC1 Value</GrandChild1>
        </Child1>
        <Child2>
            <GrandChild2>GC2 Value</GrandChild2>
        </Child2>
        <Child3>
            <GrandChild3>GC3 Value</GrandChild3>
        </Child3>
        <Child4>
            <GrandChild4>GC4 Value</GrandChild4>
        </Child4>
    </Root>
Dim grandChild3 As String = _
    (From el In root...<GrandChild3> _
    Select el).First()
Console.WriteLine(grandChild3)
```

<span data-ttu-id="c2e7e-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c2e7e-108">This example produces the following output:</span></span>

```output
GC3 Value
```

## <a name="example-find-when-the-xml-is-in-a-namespace"></a><span data-ttu-id="c2e7e-109">Exemple : Rechercher le moment où le XML se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="c2e7e-109">Example: Find when the XML is in a namespace</span></span>

<span data-ttu-id="c2e7e-110">L’exemple suivant fait la même chose que le précédent, mais pour le code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c2e7e-110">The following example does the same as the previous one, but for XML that's  in a namespace.</span></span> <span data-ttu-id="c2e7e-111">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c2e7e-111">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
  <aw:Child1>
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
  </aw:Child1>
  <aw:Child2>
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
  </aw:Child2>
  <aw:Child3>
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
  </aw:Child3>
  <aw:Child4>
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
  </aw:Child4>
</aw:Root>");
XNamespace aw = "http://www.adventure-works.com";
string grandChild3 = (string)
    (from el in root.Descendants(aw + "GrandChild3")
     select el).First();
Console.WriteLine(grandChild3);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child1>
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
                </aw:Child1>
                <aw:Child2>
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
                </aw:Child2>
                <aw:Child3>
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
                </aw:Child3>
                <aw:Child4>
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
                </aw:Child4>
            </aw:Root>
        Dim grandChild3 As String = _
            (From el In root...<aw:GrandChild3> _
            Select el).First()
        Console.WriteLine(grandChild3)
    End Sub
End Module
```

<span data-ttu-id="c2e7e-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c2e7e-112">This example produces the following output:</span></span>

```output
GC3 Value
```
