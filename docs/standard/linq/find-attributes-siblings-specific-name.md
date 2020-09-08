---
title: Comment rechercher des attributs de frères avec un nom spécifique-LINQ to XML
description: 'Découvrez comment rechercher tous les attributs qui ont un nom spécifique et qui appartient également à un frère du nœud de contexte. Deux méthodes sont affichées : l’une utilise XPathEvaluate, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: ca332f013fe8aea90b6203f5b602ab219362f5d3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553857"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-linq-to-xml"></a><span data-ttu-id="609b3-104">Comment rechercher des attributs de frères avec un nom spécifique (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="609b3-104">How to find attributes of siblings with a specific name (LINQ to XML)</span></span>

<span data-ttu-id="609b3-105">Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> pour rechercher chaque attribut ayant un nom spécifique et qui appartient également à un frère du nœud de contexte.</span><span class="sxs-lookup"><span data-stu-id="609b3-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find every attribute that has a specific name and that also belongs to a sibling of the context node.</span></span> <span data-ttu-id="609b3-106">L’article explique également comment utiliser LINQ to XML requête pour faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="609b3-106">The article also shows how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-all-sibling-elements-named-book-and-then-find-all-attributes-named-id"></a><span data-ttu-id="609b3-107">Exemple : Rechercher tous les éléments frères nommés `Book` , puis rechercher tous les attributs nommés `id`</span><span class="sxs-lookup"><span data-stu-id="609b3-107">Example: Find all sibling elements named `Book`, and then find all attributes named `id`</span></span>

<span data-ttu-id="609b3-108">Cet exemple recherche un `Book` élément dans le document XML [exemple de fichier XML : livres](sample-xml-file-books.md).</span><span class="sxs-lookup"><span data-stu-id="609b3-108">This example finds a `Book` element in XML document [Sample XML file: Books](sample-xml-file-books.md).</span></span> <span data-ttu-id="609b3-109">Il recherche ensuite tous les éléments frères nommés `Book` et tous les attributs nommés `id` de ces éléments.</span><span class="sxs-lookup"><span data-stu-id="609b3-109">It then finds all sibling elements named `Book`, and all attributes named `id` of those elements.</span></span> <span data-ttu-id="609b3-110">Le résultat est une collection d’attributs.</span><span class="sxs-lookup"><span data-stu-id="609b3-110">The result is a collection of attributes.</span></span>

<span data-ttu-id="609b3-111">L'expression XPath est `../Book/@id`.</span><span class="sxs-lookup"><span data-stu-id="609b3-111">The XPath expression is `../Book/@id`.</span></span>

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

<span data-ttu-id="609b3-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="609b3-112">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
id="bk102"
```

## <a name="see-also"></a><span data-ttu-id="609b3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="609b3-113">See also</span></span>

- [<span data-ttu-id="609b3-114">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="609b3-114">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
