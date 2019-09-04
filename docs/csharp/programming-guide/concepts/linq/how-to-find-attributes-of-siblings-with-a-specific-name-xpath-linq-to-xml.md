---
title: 'Procédure : Rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0d7842f190f7ce7869668929b69c2336d33c6183
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253735"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="ebd07-102">Procédure : Rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ebd07-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="ebd07-103">Cette rubrique montre comment rechercher tous les attributs des frères du nœud de contexte.</span><span class="sxs-lookup"><span data-stu-id="ebd07-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="ebd07-104">Seuls les attributs avec un nom spécifique sont retournés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="ebd07-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="ebd07-105">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ebd07-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="ebd07-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ebd07-106">Example</span></span>  
 <span data-ttu-id="ebd07-107">Cet exemple recherche d'abord un élément `Book`, puis tous les éléments frères nommés `Book`, puis tous les attributs nommés `id`.</span><span class="sxs-lookup"><span data-stu-id="ebd07-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="ebd07-108">Le résultat est une collection d’attributs.</span><span class="sxs-lookup"><span data-stu-id="ebd07-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="ebd07-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ebd07-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ebd07-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ebd07-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  