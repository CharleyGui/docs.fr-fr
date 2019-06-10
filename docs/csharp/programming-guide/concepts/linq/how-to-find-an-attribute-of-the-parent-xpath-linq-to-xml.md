---
title: 'Procédure : Rechercher un attribut du parent (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: f30c810483d8253132b9fe3e0959d04a8b4d26a0
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690058"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="542e6-102">Procédure : Rechercher un attribut du parent (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="542e6-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="542e6-103">Cette rubrique montre comment naviguer jusqu'à l'élément parent et rechercher un attribut de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="542e6-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="542e6-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="542e6-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="542e6-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="542e6-105">Example</span></span>

<span data-ttu-id="542e6-106">Cet exemple recherche d'abord un élément `Author`.</span><span class="sxs-lookup"><span data-stu-id="542e6-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="542e6-107">Il recherche ensuite l'attribut `id` de l'élément parent.</span><span class="sxs-lookup"><span data-stu-id="542e6-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="542e6-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="542e6-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="542e6-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="542e6-109">This example produces the following output:</span></span>

```
Results are identical
id="bk101"
```
