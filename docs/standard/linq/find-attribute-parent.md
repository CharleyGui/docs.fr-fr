---
title: Comment rechercher un attribut de l’LINQ to XML parent
description: 'Découvrez comment accéder à un élément et Rechercher un attribut de son parent. Deux méthodes sont affichées : l’une utilise XPathEvaluate, l’autre utilise LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6d5d1ce768f91aa6e32bf09668bad66f3c4f2334
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556359"
---
# <a name="how-to-find-an-attribute-of-the-parent-linq-to-xml"></a><span data-ttu-id="ed69a-104">Comment rechercher un attribut du parent (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ed69a-104">How to find an attribute of the parent (LINQ to XML)</span></span>

<span data-ttu-id="ed69a-105">Cet article explique comment utiliser <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> pour rechercher un attribut d’un élément parent, et comment utiliser LINQ to XML requête pour faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="ed69a-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find an attribute of a parent element, and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-the-author-element-and-then-find-the-id-attribute-of-its-parent"></a><span data-ttu-id="ed69a-106">Exemple : Rechercher l' `Author` élément, puis Rechercher l' `id` attribut de son parent</span><span class="sxs-lookup"><span data-stu-id="ed69a-106">Example: Find the `Author` element, and then find the `id` attribute of its parent</span></span>

<span data-ttu-id="ed69a-107">Cet exemple recherche d’abord un `Author` élément dans le document XML [exemple de fichier XML : livres](sample-xml-file-books.md), puis recherche l' `id` attribut de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="ed69a-107">This example first finds an `Author` element in XML document [Sample XML file: Books](sample-xml-file-books.md), and then finds the `id` attribute of its parent element.</span></span>

<span data-ttu-id="ed69a-108">L'expression XPath est `../@id`.</span><span class="sxs-lookup"><span data-stu-id="ed69a-108">The XPath expression is `../@id`.</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()

' LINQ to XML query
Dim att1 As XAttribute = author.Parent.Attribute("id")

' XPath expression
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _
    IEnumerable).Cast(Of XAttribute)().First()

If att1 Is att2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(att1)
```

<span data-ttu-id="ed69a-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ed69a-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```

## <a name="see-also"></a><span data-ttu-id="ed69a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed69a-110">See also</span></span>

- [<span data-ttu-id="ed69a-111">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed69a-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
