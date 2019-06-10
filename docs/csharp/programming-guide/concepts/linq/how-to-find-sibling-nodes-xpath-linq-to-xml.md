---
title: 'Procédure : Rechercher des nœuds frères (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: d225b30b8bfcae09c5824d974e194f8a06ddfc86
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485390"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="3e267-102">Procédure : Rechercher des nœuds frères (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e267-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="3e267-103">Vous souhaiterez peut-être rechercher tous les frères d'un nœud qui ont un nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="3e267-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="3e267-104">La collection résultante peut inclure le nœud de contexte si celui-ci a également le nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="3e267-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="3e267-105">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3e267-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="3e267-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e267-106">Example</span></span>  
 <span data-ttu-id="3e267-107">Cet exemple recherche d'abord un élément `Book`, puis tous les éléments frères nommés `Book`.</span><span class="sxs-lookup"><span data-stu-id="3e267-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="3e267-108">La collection résultante inclut le nœud de contexte.</span><span class="sxs-lookup"><span data-stu-id="3e267-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="3e267-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3e267-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3e267-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3e267-110">This example produces the following output:</span></span>  
  
```  
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
