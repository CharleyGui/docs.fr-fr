---
title: 'Procédure : Rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0c62ecb7660a012af556515ba5e7de330d5ab5e7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486795"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="1707b-102">Procédure : Rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1707b-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="1707b-103">Cette rubrique montre comment rechercher tous les attributs des frères du nœud de contexte.</span><span class="sxs-lookup"><span data-stu-id="1707b-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="1707b-104">Seuls les attributs avec un nom spécifique sont retournés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="1707b-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="1707b-105">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1707b-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="1707b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="1707b-106">Example</span></span>  
 <span data-ttu-id="1707b-107">Cet exemple recherche d'abord un élément `Book`, puis tous les éléments frères nommés `Book`, puis tous les attributs nommés `id`.</span><span class="sxs-lookup"><span data-stu-id="1707b-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="1707b-108">Le résultat est une collection d’attributs.</span><span class="sxs-lookup"><span data-stu-id="1707b-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="1707b-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1707b-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="1707b-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1707b-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  