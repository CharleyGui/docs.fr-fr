---
title: Guide pratique pour rechercher une Union de deux chemins d’accès d’emplacement (XPath-LINQ to XML) (C#)
description: Découvrez comment rechercher une Union de deux chemins d’accès d’emplacement XPath à l’aide d’une expression XPath. Passez en revue un exemple de code qui utilise un exemple de fichier XML.
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 65b20fe25a0990fd82ce3bd08c3433499e728512
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303320"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="2d09e-104">Guide pratique pour rechercher une Union de deux chemins d’accès d’emplacement (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2d09e-104">How to find a union of two location paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2d09e-105">XPath vous permet de rechercher l’union des résultats de deux chemins d’emplacements XPath.</span><span class="sxs-lookup"><span data-stu-id="2d09e-105">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="2d09e-106">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2d09e-106">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="2d09e-107">Vous pouvez obtenir les mêmes résultats à l'aide de l'opérateur de requête standard <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d09e-107">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d09e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d09e-108">Example</span></span>  
 <span data-ttu-id="2d09e-109">Cet exemple recherche tous les éléments `Category` et tous les éléments `Price` et il les concatène en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="2d09e-109">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="2d09e-110">Notez que la requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] appelle <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> afin d'ordonner les résultats.</span><span class="sxs-lookup"><span data-stu-id="2d09e-110">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="2d09e-111">Les résultats de l’évaluation d’expression XPath sont également dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="2d09e-111">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="2d09e-112">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2d09e-112">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="2d09e-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2d09e-113">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  