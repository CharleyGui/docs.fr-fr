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
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a>Comment rechercher les frères précédents (LINQ to XML)

Cet article montre comment utiliser <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> le long de l’axe frère précédent pour rechercher des éléments frères qui précèdent un élément donné, et comment utiliser <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> pour rechercher les mêmes éléments.

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a>Exemple : utiliser deux méthodes pour rechercher des éléments frères qui précèdent un élément

L’exemple suivant recherche l' `FullAddress` élément dans le document XML [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md), et récupère les éléments frères précédents de deux façons différentes. Il compare ensuite les résultats et les trouve identiques.

> [!NOTE]
> Les deux méthodes fournissent des résultats qui sont dans l’ordre du document.

L’expression XPath utilisée est `preceding-sibling::*` .

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

Cet exemple produit la sortie suivante :

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (Visual Basic)](./comparison-xpath-linq-xml.md)
