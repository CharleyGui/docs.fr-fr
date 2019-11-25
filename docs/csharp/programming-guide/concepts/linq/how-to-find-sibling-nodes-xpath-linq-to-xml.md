---
title: Comment rechercher des nœuds frères (XPath-LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 24bad37151f3d63b03ec28c0fbea95bef02ab614
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141015"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="10da7-102">Comment rechercher des nœuds frères (XPath-LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="10da7-102">How to find sibling nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="10da7-103">Vous souhaiterez peut-être rechercher tous les frères d'un nœud qui ont un nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="10da7-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="10da7-104">La collection résultante peut inclure le nœud de contexte si celui-ci a également le nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="10da7-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="10da7-105">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="10da7-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="10da7-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="10da7-106">Example</span></span>  
 <span data-ttu-id="10da7-107">Cet exemple recherche d'abord un élément `Book`, puis tous les éléments frères nommés `Book`.</span><span class="sxs-lookup"><span data-stu-id="10da7-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="10da7-108">La collection résultante inclut le nœud de contexte.</span><span class="sxs-lookup"><span data-stu-id="10da7-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="10da7-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="10da7-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="10da7-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="10da7-110">This example produces the following output:</span></span>  
  
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
