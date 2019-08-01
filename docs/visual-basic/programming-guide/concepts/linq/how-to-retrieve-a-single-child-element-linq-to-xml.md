---
title: 'Procédure : Récupérer un seul élément enfant (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: a1b4e5e0a6668258cef7b474c416fc572bdf2625
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710513"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="021e7-102">Procédure : Récupérer un seul élément enfant (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="021e7-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="021e7-103">Cette rubrique explique comment récupérer un seul élément enfant, étant donné le nom de l'élément enfant.</span><span class="sxs-lookup"><span data-stu-id="021e7-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="021e7-104">Lorsque vous connaissez le nom de l'élément enfant et qu'il n'y a qu'un seul élément qui possède ce nom, il peut être plus commode de récupérer un seul élément plutôt qu'une collection.</span><span class="sxs-lookup"><span data-stu-id="021e7-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="021e7-105">La méthode <xref:System.Xml.Linq.XContainer.Element%2A> retourne le premier objet <xref:System.Xml.Linq.XElement> enfant avec l'objet <xref:System.Xml.Linq.XName> spécifié.</span><span class="sxs-lookup"><span data-stu-id="021e7-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="021e7-106">Si vous souhaitez récupérer un seul élément enfant en Visual Basic, une approche courante consiste à utiliser la propriété XML, puis à récupérer le premier élément à l'aide de la notation d'indexeur de tableau.</span><span class="sxs-lookup"><span data-stu-id="021e7-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="021e7-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="021e7-107">Example</span></span>  
 <span data-ttu-id="021e7-108">L'exemple suivant illustre l'utilisation de la méthode <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="021e7-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="021e7-109">Cet exemple prend l'arborescence XML nommée `po` et recherche le premier élément nommé `Comment`.</span><span class="sxs-lookup"><span data-stu-id="021e7-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="021e7-110">L'exemple Visual Basic illustre l'utilisation de la notation d'indexeur de tableau pour récupérer un seul élément.</span><span class="sxs-lookup"><span data-stu-id="021e7-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="021e7-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Commande fournisseur standard (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="021e7-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="021e7-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="021e7-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="021e7-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="021e7-113">Example</span></span>  
 <span data-ttu-id="021e7-114">L'exemple suivant illustre le même code pour du XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="021e7-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="021e7-115">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="021e7-115">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="021e7-116">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Commande fournisseur standard dans un espace de noms](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="021e7-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="021e7-117">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="021e7-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="021e7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="021e7-118">See also</span></span>

- [<span data-ttu-id="021e7-119">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="021e7-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
