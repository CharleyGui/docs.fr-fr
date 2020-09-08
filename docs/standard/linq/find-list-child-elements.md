---
title: Comment rechercher une liste d’éléments enfants-LINQ to XML
description: Cet article compare l’axe des éléments enfants XPath à l’axe LINQ to XML XContainer. Elements.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 84b820f3192a173130c485f3e7cdadf9499932f1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553191"
---
# <a name="how-to-find-a-list-of-child-elements-linq-to-xml"></a><span data-ttu-id="e4783-103">Comment rechercher une liste d’éléments enfants (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e4783-103">How to find a list of child elements (LINQ to XML)</span></span>

<span data-ttu-id="e4783-104">Cet article compare l’axe des éléments enfants XPath à l' <xref:System.Xml.Linq.XContainer.Elements%2A> axe des LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="e4783-104">This article compares the XPath child elements axis to the LINQ to XML <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>

## <a name="example-find-all-child-elements-of-an-element"></a><span data-ttu-id="e4783-105">Exemple : Rechercher tous les éléments enfants d’un élément</span><span class="sxs-lookup"><span data-stu-id="e4783-105">Example: Find all child elements of an element</span></span>

<span data-ttu-id="e4783-106">Cet exemple recherche tous les éléments enfants de l' `Address` élément dans le document XML [exemple de fichier XML : plusieurs commandes fournisseur](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="e4783-106">This example finds all of the child elements of the `Address` element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="e4783-107">L'expression XPath est la suivante : `./*`</span><span class="sxs-lookup"><span data-stu-id="e4783-107">The XPath expression is: `./*`</span></span>

```csharp
XDocument cpo = XDocument.Load("PurchaseOrders.xml");
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");

// LINQ to XML query
IEnumerable<XElement> list1 = po.Elements();

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = po.Elements()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")

If (list1.Count() = list2.Count()) AndAlso _
    (list1.Intersect(list2).Count() = list1.Count()) Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="e4783-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e4783-108">This example produces the following output:</span></span>

```output
Results are identical
<Name>Ellen Adams</Name>
<Street>123 Maple Street</Street>
<City>Mill Valley</City>
<State>CA</State>
<Zip>10999</Zip>
<Country>USA</Country>
```

## <a name="see-also"></a><span data-ttu-id="e4783-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4783-109">See also</span></span>

- [<span data-ttu-id="e4783-110">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4783-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
