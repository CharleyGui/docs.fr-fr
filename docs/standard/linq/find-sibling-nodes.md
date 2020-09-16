---
title: Comment rechercher des nœuds frères-LINQ to XML
description: 'Découvrez comment rechercher tous les frères d’un nœud qui ont un nom spécifique. Deux méthodes sont affichées : l’une utilise XPathSelectElements, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 56833ef3758a6d8af1eb6f0a103b85ad967c9aad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555910"
---
# <a name="how-to-find-sibling-nodes-linq-to-xml"></a><span data-ttu-id="1c240-104">Comment rechercher des nœuds frères (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1c240-104">How to find sibling nodes (LINQ to XML)</span></span>

<span data-ttu-id="1c240-105">Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour rechercher tous les frères d’un nœud qui ont un nom spécifique, et comment utiliser LINQ to XML requête pour faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="1c240-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find all siblings of a node that have a specific name, and how to use LINQ to XML query to do the same thing.</span></span>

> [!NOTE]
> <span data-ttu-id="1c240-106">La collection résultante inclut le nœud de contexte s’il a également le nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="1c240-106">The resulting collection includes the context node if it also has the specific name.</span></span>

## <a name="example-find-an-element-named-book-and-all-sibling-elements-named-book"></a><span data-ttu-id="1c240-107">Exemple : Rechercher un élément nommé `Book` et tous les éléments frères nommés `Book`</span><span class="sxs-lookup"><span data-stu-id="1c240-107">Example: Find an element named `Book`, and all sibling elements named `Book`</span></span>

<span data-ttu-id="1c240-108">Cet exemple recherche d’abord un `Book` élément dans le document XML [exemple de fichier XML : livres](sample-xml-file-books.md), puis recherche tous les éléments frères nommés `Book` .</span><span class="sxs-lookup"><span data-stu-id="1c240-108">This example first finds a `Book` element in XML document [Sample XML file: Books](sample-xml-file-books.md), and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="1c240-109">La collection résultante inclut le nœud de contexte.</span><span class="sxs-lookup"><span data-stu-id="1c240-109">The resulting collection includes the context node.</span></span>

<span data-ttu-id="1c240-110">L’expression XPath est `../Book`</span><span class="sxs-lookup"><span data-stu-id="1c240-110">The XPath expression is `../Book`</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Elements("Book")
    .Skip(1)
    .First();

// LINQ to XML query
IEnumerable<XElement> list1 =
    book
    .Parent
    .Elements("Book");

// XPath expression
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>.Skip(1).First()

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")

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

<span data-ttu-id="1c240-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1c240-111">This example produces the following output:</span></span>

```output
Results are identical
<Book id="bk101">
  <Author>Garghentini, Davide</Author>
  <Title>XML Developer's Guide</Title>
  <Genre>Computer</Genre>
  <Price>44.95</Price>
  <PublishDate>2000-10-01</PublishDate>
  <Description>An in-depth look at creating applications
      with XML.</Description>
</Book>
<Book id="bk102">
  <Author>Garcia, Debra</Author>
  <Title>Midnight Rain</Title>
  <Genre>Fantasy</Genre>
  <Price>5.95</Price>
  <PublishDate>2000-12-16</PublishDate>
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
</Book>
```

## <a name="see-also"></a><span data-ttu-id="1c240-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c240-112">See also</span></span>

- [<span data-ttu-id="1c240-113">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c240-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
