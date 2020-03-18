---
title: Comment trouver des attributs de frères et sœurs avec un nom spécifique (XPath-LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 331e1a7f432f4d06b697180b1594106ec6842c9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169257"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="9b932-102">Comment trouver des attributs de frères et sœurs avec un nom spécifique (XPath-LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="9b932-102">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9b932-103">Cette rubrique montre comment rechercher tous les attributs des frères du nœud de contexte.</span><span class="sxs-lookup"><span data-stu-id="9b932-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="9b932-104">Seuls les attributs avec un nom spécifique sont retournés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="9b932-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="9b932-105">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="9b932-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="9b932-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9b932-106">Example</span></span>  
 <span data-ttu-id="9b932-107">Cet exemple recherche d'abord un élément `Book`, puis tous les éléments frères nommés `Book`, puis tous les attributs nommés `id`.</span><span class="sxs-lookup"><span data-stu-id="9b932-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="9b932-108">Le résultat est une collection d’attributs.</span><span class="sxs-lookup"><span data-stu-id="9b932-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="9b932-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9b932-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9b932-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9b932-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  