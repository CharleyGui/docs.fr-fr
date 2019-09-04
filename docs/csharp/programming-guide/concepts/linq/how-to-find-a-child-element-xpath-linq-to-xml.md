---
title: 'Procédure : Rechercher un élément enfant (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: bf0eac1e6d3a5c1c80269cb5bf3502ca51a4a6b0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253876"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="dc723-102">Procédure : Rechercher un élément enfant (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dc723-102">How to: Find a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="dc723-103">Cette rubrique compare l’axe des éléments enfants XPath à la méthode <xref:System.Xml.Linq.XContainer.Element%2A> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc723-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="dc723-104">L'expression XPath est `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="dc723-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc723-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc723-105">Example</span></span>  
 <span data-ttu-id="dc723-106">Cet exemple recherche l'élément enfant `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="dc723-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="dc723-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dc723-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="dc723-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="dc723-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  