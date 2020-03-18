---
title: Comment trouver des éléments descendants (XPath-LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: c90651502629284c67cc16de8a1aa59c392ae178
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141103"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="bca11-102">Comment trouver des éléments descendants (XPath-LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="bca11-102">How to find descendant elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="bca11-103">Cette rubrique montre comment obtenir les éléments descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="bca11-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="bca11-104">L'expression XPath est `//Name`.</span><span class="sxs-lookup"><span data-stu-id="bca11-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca11-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="bca11-105">Example</span></span>  
 <span data-ttu-id="bca11-106">Cet exemple recherche tous les descendants nommés `Name`.</span><span class="sxs-lookup"><span data-stu-id="bca11-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="bca11-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bca11-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bca11-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="bca11-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
