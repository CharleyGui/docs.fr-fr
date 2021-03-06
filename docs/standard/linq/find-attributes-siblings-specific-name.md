---
title: Comment rechercher des attributs de frères avec un nom spécifique-LINQ to XML
description: 'Découvrez comment rechercher tous les attributs qui ont un nom spécifique et qui appartient également à un frère du nœud de contexte. Deux méthodes sont affichées : l’une utilise XPathEvaluate, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 869c63f26c14bedc8d9911915b8974aa530685fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557134"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-linq-to-xml"></a>Comment rechercher des attributs de frères avec un nom spécifique (LINQ to XML)

Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> pour rechercher chaque attribut ayant un nom spécifique et qui appartient également à un frère du nœud de contexte. L’article explique également comment utiliser LINQ to XML requête pour faire la même chose.

## <a name="example-find-all-sibling-elements-named-book-and-then-find-all-attributes-named-id"></a>Exemple : Rechercher tous les éléments frères nommés `Book` , puis rechercher tous les attributs nommés `id`

Cet exemple recherche un `Book` élément dans le document XML [exemple de fichier XML : livres](sample-xml-file-books.md). Il recherche ensuite tous les éléments frères nommés `Book` et tous les attributs nommés `id` de ces éléments. Le résultat est une collection d’attributs.

L'expression XPath est `../Book/@id`.

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Element("Book");

// LINQ to XML query
IEnumerable<XAttribute> list1 =
    from el in book.Parent.Elements("Book")
    select el.Attribute("id");

// XPath expression
IEnumerable<XAttribute> list2 =
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XAttribute el in list1)
    Console.WriteLine(el);
```

```vb
Dim books as XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>(0)

' LINQ to XML query
Dim list1 As IEnumerable(Of XAttribute) = _
    From el In book.Parent.<Book> _
    Select el.Attribute("id")

' XPath expression
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()

If list1.Count() = list2.Count() And _
        (list1.Intersect(list2)).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XAttribute In list1
    Console.WriteLine(el)
Next
```

Cet exemple produit la sortie suivante :

```output
Results are identical
id="bk101"
id="bk102"
```

## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (Visual Basic)](./comparison-xpath-linq-xml.md)
