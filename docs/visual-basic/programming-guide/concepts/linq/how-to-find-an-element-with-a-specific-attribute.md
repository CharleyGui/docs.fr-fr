---
title: 'Procédure : rechercher un élément avec un attribut spécifique'
ms.date: 07/20/2015
ms.assetid: 59fb7c19-d42f-40eb-8cf8-f1d5b9658eb7
ms.openlocfilehash: ec5d3bf46d517e2cfb27c228674d9b86fefffa14
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405246"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-visual-basic"></a><span data-ttu-id="046df-102">Comment : Rechercher un élément avec un attribut spécifique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="046df-102">How to: Find an Element with a Specific Attribute (Visual Basic)</span></span>
<span data-ttu-id="046df-103">Cette rubrique montre comment rechercher un élément qui possède un attribut qui a une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="046df-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="046df-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="046df-104">Example</span></span>  
 <span data-ttu-id="046df-105">L'exemple montre comment rechercher l'élément `Address` qui possède un attribut `Type` avec la valeur « Billing ».</span><span class="sxs-lookup"><span data-stu-id="046df-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="046df-106">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="046df-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrder.xml")  
Dim address As IEnumerable(Of XElement) = _  
    From el In root.<Address> _  
    Where el.@Type = "Billing" _  
    Select el  
For Each el As XElement In address  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="046df-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="046df-107">This code produces the following output:</span></span>  
  
```xml  
          <Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
 <span data-ttu-id="046df-108">Notez que cet exemple utilise la propriété d' [axe enfant XML](../../../language-reference/xml-axis/xml-child-axis-property.md), la [propriété d’axe d’attribut XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md)et la [propriété de valeur XML](../../../language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="046df-108">Note that this example uses the [XML Child axis property](../../../language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="046df-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="046df-109">Example</span></span>  
 <span data-ttu-id="046df-110">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="046df-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="046df-111">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="046df-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="046df-112">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique dans un espace de noms](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="046df-112">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim address As IEnumerable(Of XElement) = _  
            From el In root.<aw:Address> _  
            Where el.@aw:Type = "Billing" _  
            Select el  
        For Each el As XElement In address  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="046df-113">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="046df-113">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="046df-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="046df-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="046df-115">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="046df-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="046df-116">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="046df-116">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="046df-117">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="046df-117">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
