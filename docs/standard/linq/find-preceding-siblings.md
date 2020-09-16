---
title: Recherche des frères précédents-LINQ to XML
description: 'Découvrez comment rechercher des éléments frères qui précèdent un élément donné. Deux méthodes sont affichées : l’une utilise XPathSelectElements le long de l’axe précédent-frère, l’autre utilise XNode. ElementsBeforeSelf.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 0cfd516f274eaf2940a7b944d34c6ea494e7eaa1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546188"
---
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a><span data-ttu-id="d4d71-104">Comment rechercher les frères précédents (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d4d71-104">How to find preceding siblings (LINQ to XML)</span></span>

<span data-ttu-id="d4d71-105">Cet article montre comment utiliser <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> le long de l’axe frère précédent pour rechercher des éléments frères qui précèdent un élément donné, et comment utiliser <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> pour rechercher les mêmes éléments.</span><span class="sxs-lookup"><span data-stu-id="d4d71-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> along the preceding-sibling axis to find sibling elements that precede a given element, and how to use <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> to find the same elements.</span></span>

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a><span data-ttu-id="d4d71-106">Exemple : utiliser deux méthodes pour rechercher des éléments frères qui précèdent un élément</span><span class="sxs-lookup"><span data-stu-id="d4d71-106">Example: Use two methods to find sibling elements that precede an element</span></span>

<span data-ttu-id="d4d71-107">L’exemple suivant recherche l' `FullAddress` élément dans le document XML [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md), et récupère les éléments frères précédents de deux façons différentes.</span><span class="sxs-lookup"><span data-stu-id="d4d71-107">The following example finds the `FullAddress` element in XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), and retrieves the preceding sibling elements in two different ways.</span></span> <span data-ttu-id="d4d71-108">Il compare ensuite les résultats et les trouve identiques.</span><span class="sxs-lookup"><span data-stu-id="d4d71-108">It then compares the results and finds them identical.</span></span>

> [!NOTE]
> <span data-ttu-id="d4d71-109">Les deux méthodes fournissent des résultats qui sont dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="d4d71-109">Both methods provide results that are in document order.</span></span>

<span data-ttu-id="d4d71-110">L’expression XPath utilisée est `preceding-sibling::*` .</span><span class="sxs-lookup"><span data-stu-id="d4d71-110">The XPath expression used is `preceding-sibling::*`.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");

XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");

// LINQ to XML query
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();

// XPath expression
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim add As XElement = co.<Customers>.<Customer>. _
        <FullAddress>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list2
    Console.WriteLine(el)
Next
```

<span data-ttu-id="d4d71-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d4d71-111">This example produces the following output:</span></span>

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a><span data-ttu-id="d4d71-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4d71-112">See also</span></span>

- [<span data-ttu-id="d4d71-113">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4d71-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
