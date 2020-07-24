---
title: Comment récupérer une collection d’éléments (LINQ to XML) (C#)
description: La méthode Elements en C# récupère une collection des éléments enfants d’un élément. Cet exemple LINQ to XML effectue une itération au sein des éléments enfants d’un élément.
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103359"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="4b9bd-104">Comment récupérer une collection d’éléments (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b9bd-104">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4b9bd-105">Cette rubrique illustre la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-105">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="4b9bd-106">Cette méthode récupère une collection d’éléments enfants d’un élément.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-106">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b9bd-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b9bd-107">Example</span></span>  
 <span data-ttu-id="4b9bd-108">Cet exemple itère au sein des éléments enfants de l'élément `purchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-108">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="4b9bd-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="4b9bd-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="4b9bd-110">Cet exemple produit la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-110">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b9bd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b9bd-111">See also</span></span>

- [<span data-ttu-id="4b9bd-112">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4b9bd-112">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
