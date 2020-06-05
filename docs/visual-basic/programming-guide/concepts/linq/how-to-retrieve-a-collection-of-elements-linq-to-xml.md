---
title: 'Procédure : récupérer une collection d’éléments (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 13aa9ce10df1e23ba5191b523db0272aa52ea581
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397867"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="9a225-102">Comment : récupérer une collection d’éléments (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a225-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9a225-103">Cette rubrique illustre la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a225-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="9a225-104">Cette méthode récupère une collection d’éléments enfants d’un élément.</span><span class="sxs-lookup"><span data-stu-id="9a225-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a225-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="9a225-105">Example</span></span>  
 <span data-ttu-id="9a225-106">Cet exemple itère au sein des éléments enfants de l'élément `purchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="9a225-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="9a225-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9a225-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 <span data-ttu-id="9a225-108">Cet exemple produit la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="9a225-108">This example produces the following output.</span></span>  
  
```console  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a225-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a225-109">See also</span></span>

- [<span data-ttu-id="9a225-110">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a225-110">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
