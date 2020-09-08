---
title: Comment rechercher une Union de deux chemins d’emplacement-LINQ to XML
description: 'Découvrez comment Rechercher l’Union des résultats de deux chemins d’accès d’emplacement XPath. Deux méthodes sont affichées : l’une utilise XPathSelectElements, l’autre utilise l’opérateur de requête Concat standard.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: ba2a1eef73a586074c75a7fec84c912acb8b25e9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552505"
---
# <a name="how-to-find-a-union-of-two-location-paths-linq-to-xml"></a>Comment rechercher une Union de deux chemins d’emplacement (LINQ to XML)

Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour Rechercher l’Union des résultats de deux chemins d’accès d’emplacement XPath, et comment utiliser l' <xref:System.Linq.Enumerable.Concat%2A> opérateur de requête standard pour effectuer la même opération.

## <a name="example-find-all-category-and-price-elements-and-concatenate-them"></a>Exemple : Rechercher tous `Category` les `Price` éléments et les concaténer

Cet exemple recherche tous les `Category` éléments et tous les éléments du `Price` document XML exemple de [fichier XML : données numériques](sample-xml-file-numerical-data.md), puis les concatène en une seule collection. L'expression XPath est `//Category|//Price`.

> [!NOTE]
> Le LINQ to XML les appels <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> de requête pour placer les résultats dans l’ordre du document. Les résultats de l’expression XPath sont également dans l’ordre du document.

```csharp
XDocument data = XDocument.Load("Data.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    data
    .Descendants("Category")
    .Concat(
        data
        .Descendants("Price")
    )
    .InDocumentOrder();

// XPath expression
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim data As XDocument = XDocument.Load("Data.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    data...<Category>.Concat(data...<Price>).InDocumentOrder()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = _
    data.XPathSelectElements("//Category|//Price")

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

Cet exemple produit la sortie suivante :

```output
Results are identical
<Category>A</Category>
<Price>24.50</Price>
<Category>B</Category>
<Price>89.99</Price>
<Category>A</Category>
<Price>4.95</Price>
<Category>A</Category>
<Price>66.00</Price>
<Category>B</Category>
<Price>.99</Price>
<Category>A</Category>
<Price>29.00</Price>
<Category>B</Category>
<Price>6.99</Price>
```

## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
