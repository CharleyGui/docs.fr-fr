---
title: Comment trouver un élément enfant (XPath-LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 37ce6c9d91d4edf2576ccddabd1d7f14a96b0a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141236"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="2b72f-102">Comment trouver un élément enfant (XPath-LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="2b72f-102">How to find a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2b72f-103">Ce sujet compare l’axe de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> l’élément enfant XPath à la méthode.</span><span class="sxs-lookup"><span data-stu-id="2b72f-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="2b72f-104">L'expression XPath est `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="2b72f-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b72f-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2b72f-105">Example</span></span>  
 <span data-ttu-id="2b72f-106">Cet exemple recherche l'élément enfant `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="2b72f-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="2b72f-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2b72f-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="2b72f-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2b72f-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  