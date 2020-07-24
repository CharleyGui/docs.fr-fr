---
title: Comment Rechercher l’élément racine (XPath-LINQ to XML) (C#)
description: Cet exemple C# compare XPath à LINQ to XML pour savoir comment obtenir l’élément racine d’un exemple de document XML.
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 220899823210c5cd6e9834541ca87e4d8394b4ff
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105193"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="0ce7b-103">Comment Rechercher l’élément racine (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0ce7b-103">How to find the root element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="0ce7b-104">Cette rubrique montre comment obtenir l'élément racine avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ce7b-104">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="0ce7b-105">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="0ce7b-105">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="0ce7b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="0ce7b-106">Example</span></span>  
 <span data-ttu-id="0ce7b-107">Cet exemple recherche l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="0ce7b-107">This example finds the root element.</span></span>  
  
 <span data-ttu-id="0ce7b-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0ce7b-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 <span data-ttu-id="0ce7b-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0ce7b-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
