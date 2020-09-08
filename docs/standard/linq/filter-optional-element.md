---
title: Comment filtrer sur un élément facultatif-LINQ to XML
description: Vous pouvez écrire une recherche pour un élément enfant de telle sorte que la recherche ne déclenche pas d’exception lorsque l’élément n’existe pas.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0d6aa3319efb42b467782c8f09947bdae9657ab5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552380"
---
# <a name="how-to-filter-on-an-optional-element-linq-to-xml"></a><span data-ttu-id="cd0ae-103">Comment filtrer sur un élément facultatif (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-103">How to filter on an optional element (LINQ to XML)</span></span>

<span data-ttu-id="cd0ae-104">Parfois, vous souhaitez filtrer un élément même si vous n’êtes pas certain qu’il existe dans votre document XML.</span><span class="sxs-lookup"><span data-stu-id="cd0ae-104">Sometimes you want to filter for an element even though you're not sure it exists in your XML document.</span></span> <span data-ttu-id="cd0ae-105">Vous pouvez écrire votre recherche afin que, même si l’élément particulier ne possède pas l’élément enfant, vous ne déclenchez pas une exception de référence null en le filtrant.</span><span class="sxs-lookup"><span data-stu-id="cd0ae-105">You can write your search so that, even if the particular element doesn't have the child element, you don't trigger a null reference exception by filtering for it.</span></span>

## <a name="example-search-that-doesnt-trigger-an-exception-when-the-target-element-doesnt-exist"></a><span data-ttu-id="cd0ae-106">Exemple : recherche qui ne déclenche pas d’exception lorsque l’élément cible n’existe pas</span><span class="sxs-lookup"><span data-stu-id="cd0ae-106">Example: Search that doesn't trigger an exception when the target element doesn't exist</span></span>

<span data-ttu-id="cd0ae-107">Dans l’exemple suivant, l' `Child5` élément n’a pas d' `Type` élément enfant, mais la requête s’exécute toujours correctement.</span><span class="sxs-lookup"><span data-stu-id="cd0ae-107">In the following example, the `Child5` element doesn't have a `Type` child element, but the query still executes correctly.</span></span> <span data-ttu-id="cd0ae-108">L’exemple utilise la <xref:System.Xml.Linq.Extensions.Elements%2A> méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="cd0ae-108">The example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
var cList =
    from typeElement in root.Elements().Elements("Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element("Text");
foreach(string str in cList)
    Console.WriteLine(str);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <Text>Child One Text</Text>
            <Type Value="Yes"/>
        </Child1>
        <Child2>
            <Text>Child Two Text</Text>
            <Type Value="Yes"/>
        </Child2>
        <Child3>
            <Text>Child Three Text</Text>
            <Type Value="No"/>
        </Child3>
        <Child4>
            <Text>Child Four Text</Text>
            <Type Value="Yes"/>
        </Child4>
        <Child5>
            <Text>Child Five Text</Text>
        </Child5>
    </Root>
Dim cList As IEnumerable(Of String) = _
    From typeElement In root.Elements().<Type> _
    Where typeElement.@Value = "Yes" _
    Select typeElement.Parent.<Text>.Value
Dim str As String
For Each str In cList
    Console.WriteLine(str)
Next
```

<span data-ttu-id="cd0ae-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cd0ae-109">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="example-same-search-but-for-xml-in-a-namespace"></a><span data-ttu-id="cd0ae-110">Exemple : même recherche, mais pour XML dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="cd0ae-110">Example: Same search but for XML in a namespace</span></span>

<span data-ttu-id="cd0ae-111">L’exemple suivant est la même requête, mais pour le code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cd0ae-111">The following example is the same query but for XML that's in a namespace.</span></span> <span data-ttu-id="cd0ae-112">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd0ae-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
XNamespace ad = "http://www.adatum.com";
var cList =
    from typeElement in root.Elements().Elements(ad + "Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element(ad + "Text");
foreach (string str in cList)
    Console.WriteLine(str);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child1>
                    <Text>Child One Text</Text>
                    <Type Value="Yes"/>
                </Child1>
                <Child2>
                    <Text>Child Two Text</Text>
                    <Type Value="Yes"/>
                </Child2>
                <Child3>
                    <Text>Child Three Text</Text>
                    <Type Value="No"/>
                </Child3>
                <Child4>
                    <Text>Child Four Text</Text>
                    <Type Value="Yes"/>
                </Child4>
                <Child5>
                    <Text>Child Five Text</Text>
                </Child5>
            </Root>
        Dim cList As IEnumerable(Of String) = _
            From typeElement In root.Elements().<Type> _
            Where typeElement.@Value = "Yes" _
            Select typeElement.Parent.<Text>.Value
        Dim str As String
        For Each str In cList
            Console.WriteLine(str)
        Next
    End Sub
End Module
```

<span data-ttu-id="cd0ae-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cd0ae-113">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="see-also"></a><span data-ttu-id="cd0ae-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd0ae-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cd0ae-115">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="cd0ae-116">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="cd0ae-117">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="cd0ae-118">Propriété d'axe enfant XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-118">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="cd0ae-119">Propriété d'axe d'attribut XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-119">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="cd0ae-120">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="cd0ae-120">XML Value Property</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="cd0ae-121">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="cd0ae-122">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd0ae-122">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
