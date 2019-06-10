---
title: 'Procédure : Rechercher des éléments descendants (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: 99f5f552935d6169537ccfbadff2a21396828e47
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486774"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="fd85e-102">Procédure : Rechercher des éléments descendants (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fd85e-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="fd85e-103">Cette rubrique montre comment obtenir les éléments descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="fd85e-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="fd85e-104">L'expression XPath est `//Name`.</span><span class="sxs-lookup"><span data-stu-id="fd85e-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd85e-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd85e-105">Example</span></span>  
 <span data-ttu-id="fd85e-106">Cet exemple recherche tous les descendants nommés `Name`.</span><span class="sxs-lookup"><span data-stu-id="fd85e-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="fd85e-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fd85e-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="fd85e-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd85e-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
