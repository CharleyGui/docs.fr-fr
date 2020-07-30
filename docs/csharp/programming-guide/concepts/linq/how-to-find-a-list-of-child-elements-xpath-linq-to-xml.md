---
title: Comment rechercher une liste d’éléments enfants (XPath-LINQ to XML) (C#)
description: Découvrez comment rechercher une liste d’éléments enfants à l’aide d’une expression XPath. Passez en revue un exemple de code qui recherche tous les éléments enfants d’un élément spécifique.
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: a3025aca7fb1055acd55e5ce98914d8359ebe4b7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301721"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="1ef6c-104">Comment rechercher une liste d’éléments enfants (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1ef6c-104">How to find a list of child elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="1ef6c-105">Cette rubrique compare l’axe des éléments enfants XPath à l' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axe.</span><span class="sxs-lookup"><span data-stu-id="1ef6c-105">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="1ef6c-106">L'expression XPath est la suivante : `./*`</span><span class="sxs-lookup"><span data-stu-id="1ef6c-106">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef6c-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ef6c-107">Example</span></span>  
 <span data-ttu-id="1ef6c-108">Cet exemple recherche tous les éléments enfants de l'élément `Address`.</span><span class="sxs-lookup"><span data-stu-id="1ef6c-108">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="1ef6c-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1ef6c-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="1ef6c-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1ef6c-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
