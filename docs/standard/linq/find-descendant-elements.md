---
title: Comment rechercher des éléments descendants-LINQ to XML
description: Cet article montre comment utiliser XPath et LINQ to XML requête, en C# et Visual Basic, pour rechercher tous les éléments descendants portant un nom spécifié.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: 61c3ff3fa0b41301215e6f627d76681ad03aa938
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552345"
---
# <a name="how-to-find-descendant-elements-linq-to-xml"></a><span data-ttu-id="82d9a-103">Comment rechercher des éléments descendants (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="82d9a-103">How to find descendant elements (LINQ to XML)</span></span>

<span data-ttu-id="82d9a-104">Cet article montre comment utiliser XPath et LINQ to XML requête, en C# et Visual Basic, pour rechercher tous les éléments descendants portant un nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="82d9a-104">This article shows how to use XPath and LINQ to XML query, in C# and Visual Basic, to find all descendant elements that have a specified name.</span></span>

## <a name="example-find-descendant-elements-that-have-a-specified-name"></a><span data-ttu-id="82d9a-105">Exemple de recherche d’éléments descendants portant un nom spécifié</span><span class="sxs-lookup"><span data-stu-id="82d9a-105">Example Find descendant elements that have a specified name</span></span>

 <span data-ttu-id="82d9a-106">Cet exemple montre comment utiliser LINQ to XML Query et XPath pour rechercher tous les éléments descendants nommés `Name` dans le document XML [exemple de fichier XML : plusieurs commandes fournisseur](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="82d9a-106">This example shows how to use LINQ to XML query and XPath to find all descendant elements named `Name` in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span> <span data-ttu-id="82d9a-107">L'expression XPath est `//Name`.</span><span class="sxs-lookup"><span data-stu-id="82d9a-107">The XPath expression is `//Name`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
IEnumerable<XElement> list1 = po.Root.Descendants("Name");

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = po...<Name>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")

If (list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count()) Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="82d9a-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="82d9a-108">This example produces the following output:</span></span>

```output
Results are identical
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

## <a name="see-also"></a><span data-ttu-id="82d9a-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d9a-109">See also</span></span>

- [<span data-ttu-id="82d9a-110">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82d9a-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)