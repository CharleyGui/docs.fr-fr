---
title: Comment Rechercher l’élément racine (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1c5526f436b5b9d88ca359ef7e0fc04c5c3cf43c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345950"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="cb062-102">Comment Rechercher l’élément racine (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cb062-102">How to find the root element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="cb062-103">Cette rubrique montre comment obtenir l'élément racine avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb062-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="cb062-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="cb062-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="cb062-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb062-105">Example</span></span>  
 <span data-ttu-id="cb062-106">Cet exemple recherche l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="cb062-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="cb062-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cb062-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="cb062-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cb062-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
