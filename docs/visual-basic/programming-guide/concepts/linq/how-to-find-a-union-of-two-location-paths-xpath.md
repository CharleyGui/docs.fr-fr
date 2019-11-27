---
title: 'Comment : rechercher une union de deux chemins d’emplacements (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: db9ba3f66bfa8643738203ec05a106bab4193fda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352982"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="436fb-102">Comment : Rechercher une Union de deux chemins d’accès d’emplacement (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="436fb-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="436fb-103">XPath vous permet de rechercher l’union des résultats de deux chemins d’emplacements XPath.</span><span class="sxs-lookup"><span data-stu-id="436fb-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="436fb-104">L'expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="436fb-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="436fb-105">Vous pouvez obtenir les mêmes résultats à l'aide de l'opérateur de requête standard <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="436fb-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="436fb-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="436fb-106">Example</span></span>  
 <span data-ttu-id="436fb-107">Cet exemple recherche tous les éléments `Category` et tous les éléments `Price` et il les concatène en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="436fb-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="436fb-108">Notez que la requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] appelle <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> afin d'ordonner les résultats.</span><span class="sxs-lookup"><span data-stu-id="436fb-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="436fb-109">Les résultats de l’évaluation d’expression XPath sont également dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="436fb-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="436fb-110">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="436fb-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="436fb-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="436fb-111">This example produces the following output:</span></span>  
  
```console
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
  
## <a name="see-also"></a><span data-ttu-id="436fb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="436fb-112">See also</span></span>

- [<span data-ttu-id="436fb-113">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="436fb-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
