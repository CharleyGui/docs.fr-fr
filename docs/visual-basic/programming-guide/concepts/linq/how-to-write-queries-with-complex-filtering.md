---
title: 'Procédure : écrire des requêtes avec un filtrage complexe'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 18ed4379b7ec9c8007cc3c189fc45571b5161911
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397620"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="8bf10-102">Comment : écrire des requêtes avec un filtrage complexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf10-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="8bf10-103">Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes.</span><span class="sxs-lookup"><span data-stu-id="8bf10-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="8bf10-104">Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8bf10-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="8bf10-105">Cette rubrique fournit un exemple d'écriture de requête avec un filtrage complexe.</span><span class="sxs-lookup"><span data-stu-id="8bf10-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bf10-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="8bf10-106">Example</span></span>  
 <span data-ttu-id="8bf10-107">Cet exemple montre comment rechercher tous les éléments `PurchaseOrder` qui ont un élément `Address` enfant ayant un attribut `Type` égal à « Shipping » et un élément `State` enfant égal à « NY ».</span><span class="sxs-lookup"><span data-stu-id="8bf10-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="8bf10-108">Il utilise une sous-requête dans la clause `Where` et l'opérateur `Any` retourne `True` si la collection possède des éléments.</span><span class="sxs-lookup"><span data-stu-id="8bf10-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="8bf10-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8bf10-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8bf10-110">Pour plus d’informations sur l' `Any` opérateur, consultez [opérations de quantificateur (Visual Basic)](quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8bf10-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="8bf10-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8bf10-111">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="8bf10-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="8bf10-112">Example</span></span>  
 <span data-ttu-id="8bf10-113">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8bf10-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8bf10-114">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8bf10-114">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8bf10-115">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur dans un espace de noms](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="8bf10-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="8bf10-116">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8bf10-116">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bf10-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bf10-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="8bf10-118">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf10-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="8bf10-119">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="8bf10-119">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="8bf10-120">XML Attribute Axis Property</span><span class="sxs-lookup"><span data-stu-id="8bf10-120">XML Attribute Axis Property</span></span>](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="8bf10-121">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="8bf10-121">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="8bf10-122">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf10-122">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
- [<span data-ttu-id="8bf10-123">Opérations de quantificateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf10-123">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)
