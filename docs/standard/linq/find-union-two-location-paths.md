---
title: Comment rechercher une Union de deux chemins d’emplacement-LINQ to XML
description: 'Découvrez comment Rechercher l’Union des résultats de deux chemins d’accès d’emplacement XPath. Deux méthodes sont affichées : l’une utilise XPathSelectElements, l’autre utilise l’opérateur de requête Concat standard.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 13d1a22d933d789f28efa2d196fc0106986caa90
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555006"
---
# <a name="how-to-find-a-union-of-two-location-paths-linq-to-xml"></a><span data-ttu-id="6a03c-104">Comment rechercher une Union de deux chemins d’emplacement (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6a03c-104">How to find a union of two location paths (LINQ to XML)</span></span>

<span data-ttu-id="6a03c-105">Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour Rechercher l’Union des résultats de deux chemins d’accès d’emplacement XPath, et comment utiliser l' <xref:System.Linq.Enumerable.Concat%2A> opérateur de requête standard pour effectuer la même opération.</span><span class="sxs-lookup"><span data-stu-id="6a03c-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find the union of the results of two XPath location paths, and how to use the <xref:System.Linq.Enumerable.Concat%2A> standard query operator to do the same thing.</span></span>

## <a name="example-find-all-category-and-price-elements-and-concatenate-them"></a><span data-ttu-id="6a03c-106">Exemple : Rechercher tous `Category` les `Price` éléments et les concaténer</span><span class="sxs-lookup"><span data-stu-id="6a03c-106">Example: Find all `Category` and `Price` elements and concatenate them</span></span>

<span data-ttu-id="6a03c-107">Cet exemple recherche tous les `Category` éléments et tous les éléments du `Price` document XML exemple de [fichier XML : données numériques](sample-xml-file-numerical-data.md), puis les concatène en une seule collection.</span><span class="sxs-lookup"><span data-stu-id="6a03c-107">This example finds all of the `Category` elements and all of the `Price` elements in XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md), and concatenates them into a single collection.</span></span> <span data-ttu-id="6a03c-108">L'expression XPath est `//Category|//Price`.</span><span class="sxs-lookup"><span data-stu-id="6a03c-108">The XPath expression is `//Category|//Price`.</span></span>

> [!NOTE]
> <span data-ttu-id="6a03c-109">Le LINQ to XML les appels <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> de requête pour placer les résultats dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="6a03c-109">The LINQ to XML query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to put the results in document order.</span></span> <span data-ttu-id="6a03c-110">Les résultats de l’expression XPath sont également dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="6a03c-110">The XPath expression results are also in document order.</span></span>

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

<span data-ttu-id="6a03c-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6a03c-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6a03c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a03c-112">See also</span></span>

- [<span data-ttu-id="6a03c-113">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a03c-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
