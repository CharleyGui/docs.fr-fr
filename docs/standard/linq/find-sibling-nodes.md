---
title: Comment rechercher des nœuds frères-LINQ to XML
description: 'Découvrez comment rechercher tous les frères d’un nœud qui ont un nom spécifique. Deux méthodes sont affichées : l’une utilise XPathSelectElements, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 3c764cec818cf788282bb616cc123e9be8d62c08
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552540"
---
# <a name="how-to-find-sibling-nodes-linq-to-xml"></a>Comment rechercher des nœuds frères (LINQ to XML)

Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour rechercher tous les frères d’un nœud qui ont un nom spécifique, et comment utiliser LINQ to XML requête pour faire la même chose.

> [!NOTE]
> La collection résultante inclut le nœud de contexte s’il a également le nom spécifique.

## <a name="example-find-an-element-named-book-and-all-sibling-elements-named-book"></a>Exemple : Rechercher un élément nommé `Book` et tous les éléments frères nommés `Book`

Cet exemple recherche d’abord un `Book` élément dans le document XML [exemple de fichier XML : livres](sample-xml-file-books.md), puis recherche tous les éléments frères nommés `Book` . La collection résultante inclut le nœud de contexte.

L’expression XPath est `../Book`

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

Cet exemple produit la sortie suivante :

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

## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
