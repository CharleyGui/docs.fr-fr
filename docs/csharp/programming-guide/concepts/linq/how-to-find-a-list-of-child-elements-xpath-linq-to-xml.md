---
title: 'Procédure : Rechercher une liste d’éléments enfants (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 63b0fec504ff8424e9e96318c46191a150b72f46
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253835"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="59c8f-102">Procédure : Rechercher une liste d’éléments enfants (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="59c8f-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="59c8f-103">Cette rubrique compare l’axe des éléments enfants XPath à l’axe <xref:System.Xml.Linq.XContainer.Elements%2A> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59c8f-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="59c8f-104">L'expression XPath est la suivante : `./*`</span><span class="sxs-lookup"><span data-stu-id="59c8f-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="59c8f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="59c8f-105">Example</span></span>  
 <span data-ttu-id="59c8f-106">Cet exemple recherche tous les éléments enfants de l'élément `Address`.</span><span class="sxs-lookup"><span data-stu-id="59c8f-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="59c8f-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="59c8f-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Elements();  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="59c8f-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="59c8f-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
